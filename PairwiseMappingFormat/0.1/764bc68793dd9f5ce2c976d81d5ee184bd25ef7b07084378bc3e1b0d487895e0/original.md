```
query_coverage(rec::Record) -> Float64
```

Compute the fraction of the query covered by the alignment.

# Examples

```jldoctest
julia> query_coverage(record)
0.9999535124653004
```

See also: [`target_coverage`](@ref), [`aln_identity`](@ref)
