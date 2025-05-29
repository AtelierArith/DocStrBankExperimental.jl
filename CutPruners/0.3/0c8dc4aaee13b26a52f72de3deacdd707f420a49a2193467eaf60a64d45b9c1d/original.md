```
addposition!(man::DeMatosCutPruner, position::Matrix)
```

Update territories with cuts previously computed during backward pass.

# Arguments

  * `man::DeMatosCutPruner`   Pruner to update.
  * `position::Array{T, 2}`   New visited positions, corresponding to a collection of points.
