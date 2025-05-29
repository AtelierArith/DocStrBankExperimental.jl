```
to_sized(sys::AbstractStateSpace)
```

Return a [`HeteroStateSpace`](@ref) where the system matrices are of type SizedMatrix.

*NOTE: This function is fundamentally type unstable.* For maximum performance, create the sized system manually, or make use of the function-barrier technique.
