# RPTree

The struct RPTree stores the list of event that occurred during tree construction.  The parameters used to grow the tree are stored in field argument.

FIELDS

  * treedata : the Tree
  * argument : the parameters describing tree growing
  * eventDict : the event that occured in each node.
  * treelock : a lock to manipulate eventDict
