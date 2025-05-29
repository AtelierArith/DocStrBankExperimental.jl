```
walk(fn::Function, x)
```

A generic dispatch-based tree-walker which applies `fn::Function` to `x`, specialized to `Code` node types (like `Core.ReturnNode`, `Core.GotoNode`, `Core.GotoIfNot`, etc). Applies `fn::Function` to sub-fields of nodes, and then zips the result back up into the node.
