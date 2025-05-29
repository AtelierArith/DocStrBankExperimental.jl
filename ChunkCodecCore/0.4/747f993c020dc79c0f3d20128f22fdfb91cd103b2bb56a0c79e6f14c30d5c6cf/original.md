```
decoded_size_range(e)::StepRange{Int64, Int64}
```

Return the range of allowed `src` sizes for encoding.

[`encode_bound`](@ref) on any value in the returned range must be in `0:typemax(Int64)-1`.

See also [`encode_bound`](@ref)
