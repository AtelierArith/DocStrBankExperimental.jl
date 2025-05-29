Fill an ACSet

Adds parts for a given part `part` up to a given number `n`. Unlike `add_part!`, this is idempotent.

Example:

Consider a cycle graph `g` with 3 vertices and 3 edges. Then

```
ensure_size!(g, :V, 5) # = 4:5
```

adds vertices 4 and 5. Suppose instead we added an edge,

```
ensure_size!(g, :E, 4) # = 4:4
```

Repeating this operation, we see that no new edges are added.

```
ensure_size!(g, :E, 4) # = 1:0
```
