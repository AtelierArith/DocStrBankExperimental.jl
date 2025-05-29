```
present(t::Union{Real, Missing}, minabundance::Real=0.0)
present(at::AbstractAbundanceTable, minabundance::Real=0.0)
```

Check if a given (non-zero) value is greater than or equal to a minimum value. If the minimum abundance is 0, just checks if value is non-zero.

If used on an `AbstractAbundanceTable`, returns a sparse boolean matrix of the same size.
