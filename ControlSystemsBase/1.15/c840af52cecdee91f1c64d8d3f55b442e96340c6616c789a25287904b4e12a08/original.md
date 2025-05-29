```
StaticStateSpace(sys::AbstractStateSpace)
```

Return a [`HeteroStateSpace`](@ref) where the system matrices are of type SMatrix.

*NOTE: This function is fundamentally type unstable.* For maximum performance, create the static system manually, or make use of the function-barrier technique.
