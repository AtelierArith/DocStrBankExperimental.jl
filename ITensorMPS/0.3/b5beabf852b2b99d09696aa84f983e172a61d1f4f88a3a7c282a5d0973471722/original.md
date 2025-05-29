```
siteind(::typeof(first), M::Union{MPS,MPO}, j::Integer; kwargs...)
```

Return the first site Index found on the MPS or MPO (the first Index unique to the `j`th MPS/MPO tensor).

You can choose different filters, like prime level and tags, with the `kwargs`.
