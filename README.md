# ns3
On this page, we will try to summarize current ns-3 development work. If you are interested in collaborating on one of these projects, or reviewing work by others, please do not hesitate to contact the individuals identified, or the page maintainer.

There are a few other places to look for current activity on ns-3 development:

the current release page will list code under consideration for merging, and bugs being worked. The next release, ns-3.30 release, is not yet scheduled.
we should have entries for all of our known bugs in the Bugzilla bug tracker.
Related projects list some active and past projects that are associated with ns-3.
We maintain a suggested project ideas page for people interested in trying to start something new, or finish off some existing work.
We conduct code review discussions on the Google Group 'ns-3-reviews'
// Java program to check if binary tree is subtree of another binary tree 

// A binary tree node 
class Node 
{ 
	int data; 
	Node left, right, nextRight; 

	Node(int item) 
	{ 
		data = item; 
		left = right = nextRight = null; 
	} 
} 

class BinaryTree 
{ 
	Node root1,root2; 

	/* A utility function to check whether trees with roots as root1 and 
	root2 are identical or not */
	boolean areIdentical(Node root1, Node root2) 
	{ 

		/* base cases */
		if (root1 == null && root2 == null) 
			return true; 

		if (root1 == null || root2 == null) 
			return false; 

		/* Check if the data of both roots is same and data of left and right 
		subtrees are also same */
		return (root1.data == root2.data 
				&& areIdentical(root1.left, root2.left) 
				&& areIdentical(root1.right, root2.right)); 
	} 

	/* This function returns true if S is a subtree of T, otherwise false */
	boolean isSubtree(Node T, Node S) 
	{ 
		/* base cases */
		if (S == null) 
			return true; 

		if (T == null) 
			return false; 

		/* Check the tree with root as current node */
		if (areIdentical(T, S)) 
			return true; 

		/* If the tree with root as current node doesn't match then 
		try left and right subtrees one by one */
		return isSubtree(T.left, S) 
				|| isSubtree(T.right, S); 
	} 

	public static void main(String args[]) 
	{ 
		BinaryTree tree = new BinaryTree(); 
		
		// TREE 1 
		/* Construct the following tree 
			26 
			/ \ 
			10	 3 
		/ \	 \ 
		4	 6	 3 
		\ 
			30 */
			
		tree.root1 = new Node(26); 
		tree.root1.right = new Node(3); 
		tree.root1.right.right = new Node(3); 
		tree.root1.left = new Node(10); 
		tree.root1.left.left = new Node(4); 
		tree.root1.left.left.right = new Node(30); 
		tree.root1.left.right = new Node(6); 

		// TREE 2 
		/* Construct the following tree 
		10 
		/ \ 
		4	 6 
		\ 
		30 */
			
		tree.root2 = new Node(10); 
		tree.root2.right = new Node(6); 
		tree.root2.left = new Node(4); 
		tree.root2.left.right = new Node(30); 

		if (tree.isSubtree(tree.root1, tree.root2)) 
			System.out.println("Tree 2 is subtree of Tree 1 "); 
		else
			System.out.println("Tree 2 is not a subtree of Tree 1"); 
	} 
} 

// This code has been contributed by Mayank Jaiswal 
