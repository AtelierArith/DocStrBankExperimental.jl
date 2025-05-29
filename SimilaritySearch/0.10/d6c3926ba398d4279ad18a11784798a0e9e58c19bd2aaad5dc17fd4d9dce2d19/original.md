```
optimize!(
    index::AbstractSearchIndex,
    kind::ErrorFunction=ParetoRecall(),
    space::AbstractSolutionSpace=optimization_space(index);
    kwargs...)
    optimize_index!(index, kind, space; kwargs...)
```

A frontend function for [`optimize_index!`](@ref) which can be specialized for some particular index, kinds or spaces.
