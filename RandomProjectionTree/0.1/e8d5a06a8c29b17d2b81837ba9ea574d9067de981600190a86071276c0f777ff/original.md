# TreeNode{T,U}

## FIELDS

a Treenode consists in

  * an array of data of generic struct T for which there must exist a Distance.
  * depth : depth in tree , root node is at depth 0.
  * rankInParent : where a node is in parent.children field
  * possibly a parent node
  * an array of children node.
  * some private data of type U for possible use by application using Tree.

## CONSTRUCTORS

1. `function TreeNode{T,U}(parentArg::TreeNode{T,U}, dataArg::T)`.       full constructor with parent node specified and data
2. `function TreeNode{T,U}(dataArg::T, privatedata::U)`.      constructor for root node (without parent).
3. `function TreeNode{T, U}(dataArg::T)`
