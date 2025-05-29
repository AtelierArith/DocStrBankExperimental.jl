```
swap_node(expr::AbstractRuleNode, new_expr::AbstractRuleNode, path::Vector{Int})
```

Replace a node in `expr`, specified by `path`, with `new_expr`. Path is a sequence of child indices, starting from the root node.
