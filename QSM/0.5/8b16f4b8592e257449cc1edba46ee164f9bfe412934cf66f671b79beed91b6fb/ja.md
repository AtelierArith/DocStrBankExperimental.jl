```
unpadarray(
    xp::AbstractArray{T, N},
    sz::NTuple{N, Integer}
) -> typeof(similar(xp, sz))
```

`xp`から`n÷2+1`を中心としたサイズ`sz`の配列を抽出します。
