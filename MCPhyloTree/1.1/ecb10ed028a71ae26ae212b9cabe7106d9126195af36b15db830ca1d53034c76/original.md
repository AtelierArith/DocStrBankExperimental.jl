```
set_binary!(root::T)  where T <: GeneralNode
```

Assign a binary representation to each node, which specifies the path from the root to this node via the binary representation of the node. A left turn is a 1 in binary and a right turn a 0.
