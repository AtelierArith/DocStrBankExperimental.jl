```
children(node::InfoNode)
```

Return for each `node` given, its children. 

In case of a `DecisionTree` there are always exactly two children, because  the model produces binary trees where all nodes have exactly one left and  one right child. `children` is used for tree traversal.

The additional information `info` is carried over from `node` to its children.
