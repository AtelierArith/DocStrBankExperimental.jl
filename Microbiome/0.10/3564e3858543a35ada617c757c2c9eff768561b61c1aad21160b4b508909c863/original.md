```
prevalence(a::AbstractArray{<:Real}, minabundance::Real=0.0)
prevalence(at::AbstractAbundanceTable, minabundance::Real=0.0)
```

Return the fraction of values that are greater than or equal to a minimum. If the minimum abundance is 0, returns the fraction of non-zero values.

If used on an `AbstractAbundanceTable`, returns a prevalence value for each `feature` accross the `sample`s.
