public class pre {
    static class Node {
        int data;
        Node Left;
        Node Right;

        Node(int data) {
            this.data = data;
            this.Left = null;

        }

        public static class BinaryTree {
            static int idx = -1;
            static Node BuildTree(int[] Node) {
                idx++;
                if (Node[idx] == -1) {
                    return null;

                }
                Node NewNode = new Node(Node[idx]);
                NewNode.Left = BuildTree(Node);
                NewNode.Right = BuildTree(Node);

                return NewNode;


            }

            public static void PreOrder(Node Root) {
                if (Root == null) {
                    return;

                }
                System.out.println(Root.data + "");
                PreOrder(Root.Left);
                PreOrder(Root.Right);
                return;

            }

            public static void InOrder(Node Root) {
                if (Root == null) {
                    return;
                }
                InOrder(Root.Left);
                System.out.println(Root.data + "");
                InOrder(Root.Right);
                return;

            }

            public static void PostOrder(Node Root) {
                if (Root == null) {
                    return;

                }
                PostOrder(Root.Left);
                PostOrder(Root.Right);
                System.out.println(Root.data);
                return;

            }

            public static int CountOfNodes(Node Root) {
                if (Root == null) {
                    return 0;
                }
                int LeftNode = CountOfNodes(Root.Left);
                int RightNode = CountOfNodes(Root.Right);

                return LeftNode + RightNode + 1;

            }

            public static int SumOfNodes(Node Root) {
                if (Root == null) {
                    return 0;

                }
                int LeftNode = SumOfNodes(Root.Left);
                int RIghtNode = SumOfNodes(Root.Right);

                return LeftNode + RIghtNode + Root.data;
            }

            public static int Height(Node Root) {
                if (Root == null) {
                    return 0;
                }
                int LeftHeight = Height(Root.Left);
                int RightHeight = Height(Root.Right);
                int MyHeight = Math.max(LeftHeight, RightHeight + 1);
                return MyHeight;

            }

            public static int Diameter(Node Root) {
                if (Root == null) {
                    return 0;

                }
                int Diam1 = Height(Root.Left);
                int Diam2 = Height(Root.Right);
                int Diam3 = Height(Root.Left) + Height(Root.Right) + 1;
                return Math.max(Height(Diam3), Math.max(Height(Diam1, Diam2)));


            }

            static class Info {
                int ht;
                int Diam;

                Info(int ht, int Diam) {
                    this.ht = ht;
                    this.Diam = Diam;
                }
            }

            public static Info Diameter2(Node Root) {
                if (Root == null) {
                    return 0;

                }
                Info Left = Diameter2(Root.Left);
                Info Right = Diameter2(Root.Right);

                int MyHeight = Math.max(Left.ht, Right.ht + 1);

                int Diam1 = Left.Diam;
                int Diam2 = Right.Diam;
                int Diam3 = Left.Diam + Right.Diam + 1;

                int MyDiam = Math.max(Math.max(Diam1, Diam2), Diam3);

                Info Infor = new Info(MyHeight, MyDiam);
                return Infor;


            }

            public static void main(String[] args) {
                int Node[] = {1, 2, 3, -1, -1, 4, 5, -1, -1, 6};
                BinaryTree tree = new BinaryTree();
                Node Root = tree.BuildTree(Node);
                System.out.println(Root.data);
            }
        }
    }
}
