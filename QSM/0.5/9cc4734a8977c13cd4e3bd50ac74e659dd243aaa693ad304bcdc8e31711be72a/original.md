```
unpadarray!(
    x::AbstractArray{Tx, N},
    xp::AbstractArray{Txp, N},
    sz::NTuple{N, Integer}
) -> x
```

Extract array centered at `n÷2+1` from `xp` into `x`.
