```
is_segment(node)
```

Checks if a node (n) has only one child (n+1). This is usefull to simplify a complex mtg to become an mtg with nodes only at the branching points, has it is often measured on the field.

The function also takes care of passing the link of the node (n) to its child (n+1) if the node (n) branches or decompose its parent (n-1). This allows a conservation of the relationships as they previously were in the mtg.

See [`delete_nodes!`](@ref) for an example of application.
