```
Node
```

This data type holds the basic Node structure. The type T is used to specify the type of the data stored in the node.

  * If `nchild` is `0` the Node is a leaf node.
  * If `root` is `False` the Node is a child of another node.
  * `inc_length` specifies the length of the incomming branch.
  * `binary` specifies the path from the root to the Node. `1` and `0` represent left and right turns respectively.
