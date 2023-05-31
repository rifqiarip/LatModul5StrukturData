import java.util.Scanner;

class TreeNode {
    int data;
    TreeNode left;
    TreeNode right;

    public TreeNode(int data) {
        this.data = data;
        this.left = null;
        this.right = null;
    }
}

class BinaryTree {
    private TreeNode root;

    public void insert(int data) {
        root = insertNode(root, data);
    }

    private TreeNode insertNode(TreeNode node, int data) {
        if (node == null) {
            return new TreeNode(data);
        } else {
            if (data <= node.data) {
                node.left = insertNode(node.left, data);
            } else {
                node.right = insertNode(node.right, data);
            }
            return node;
        }
    }

    public void traversePreorder() {
        System.out.print("Preorder Traversal: ");
        traversePreorder(root);
        System.out.println();
    }

    private void traversePreorder(TreeNode node) {
        if (node != null) {
            System.out.print(node.data + " ");
            traversePreorder(node.left);
            traversePreorder(node.right);
        }
    }

    public void traverseInorder() {
        System.out.print("Inorder Traversal: ");
        traverseInorder(root);
        System.out.println();
    }

    private void traverseInorder(TreeNode node) {
        if (node != null) {
            traverseInorder(node.left);
            System.out.print(node.data + " ");
            traverseInorder(node.right);
        }
    }

    public void traversePostorder() {
        System.out.print("Postorder Traversal: ");
        traversePostorder(root);
        System.out.println();
    }

    private void traversePostorder(TreeNode node) {
        if (node != null) {
            traversePostorder(node.left);
            traversePostorder(node.right);
            System.out.print(node.data + " ");
        }
    }
}


public class Main {
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        Scanner scanner = new Scanner(System.in);
        System.out.print("Masukkan kombinasi (huruf dan angka) secara terpisah (gunakan spasi sebagai pemisah): ");
        String input = scanner.nextLine();
        String[] elements = input.split(" ");

        for (String element : elements) {
            int data;
            try {
                data = Integer.parseInt(element);
                tree.insert(data);
            } catch (NumberFormatException e) {
                System.out.println("Input tidak valid: " + element);
            }
        }

        tree.traversePreorder();
        tree.traverseInorder();
        tree.traversePostorder();
    }
}
