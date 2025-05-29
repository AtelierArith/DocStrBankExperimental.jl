```
unpadarray!(
    x::AbstractArray{Tx, N},
    xp::AbstractArray{Txp, N},
    sz::NTuple{N, Integer}
) -> x
```

`xp` から `n÷2+1` を中心とした配列を `x` に抽出します。
