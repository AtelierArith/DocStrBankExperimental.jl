```
unpadarray(
    xp::AbstractArray{T, N},
    sz::NTuple{N, Integer}
) -> typeof(similar(xp, sz))
```

Extract array of size `sz` centered at `n÷2+1` from `xp`.
