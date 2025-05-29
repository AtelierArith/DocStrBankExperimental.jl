```
Repair(K)
```

Perform repairing operation with code `K`.

## Available operations

  * K =  0: duplicated vertices and faces are removed
  * K =  1: unused vertices are removed
  * K =  2: non-manifold faces are removed
  * K =  3: degenerate faces are removed
  * K =  4: non-manifold vertices are removed
  * K =  5: non-manifold vertices are split by threshold
  * K =  6: close vertices are merged (given a radius)
  * K =  7: faces are coherently oriented
  * K =  8: zero-area ears are removed
  * K =  9: rings of polygon are sorted
  * K = 10: outer rings of polygon are expanded
  * K = 11: rings of polygon are coherently oriented
  * K = 12: degenerate rings of polygon are removed

## Examples

```
# remove duplicates and degenerates
mesh |> Repair(0) |> Repair(3)
```
