```
jacobian!(∇c, con::AbstractConstraint, Z, [inds])
```

Evaluate constraints for entire trajectory. This is the most general method used to evaluate constraints along the trajectory `Z`, and should be the one used in other functions. The `inds` argument determines at which knot points the constraint is evaluated.

The values are stored in `∇c`, which should be a matrix of matrices. If `con` is a `StageConstraint`, `size(∇c,2) = 1`, and `size(∇c,2) = 2` if `con` is a `CoupledConstraint`.

If `con` is a `StageConstraint`, this will call `jacobian!(∇c, con, z)` by default, or `jacobian!(∇c, con, z1, z2, i)` if `con` is a `CoupledConstraint`.
