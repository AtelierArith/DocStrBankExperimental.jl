```
evaluate!(b::AbstractVector, B::BSplineBasis, i::Integer,
          x::AbstractVector, args...)
```

i 番目の基底関数を位置 `x` で評価し、結果を `b` に書き込みます。

詳細は [`evaluate`](@ref) を参照してください。
