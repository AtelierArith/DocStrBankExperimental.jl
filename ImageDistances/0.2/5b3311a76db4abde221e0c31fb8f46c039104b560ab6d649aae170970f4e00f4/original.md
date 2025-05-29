```
GenericHausdorff(inner_op, outer_op, weights = nothing)
```

The generalized Hausdorff distance with inner reduction `inner_op` and outer reduction `outer_op`. Optionally, `weights` can be used for each axis before distance transformations are applied.

## References

Dubuisson, M-P; Jain, A. K., 1994. *A Modified Hausdorff Distance for Object-Matching*.

See also: [`Hausdorff`](@ref), [`ModifiedHausdorff`](@ref)
