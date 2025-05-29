```
Taylor1{T<:Number} <: AbstractSeries{T}
```

1つの独立変数における多項式展開のデータ型。

**フィールド:**

  * `coeffs :: Array{T,1}` 展開係数; $i$-番目の成分は展開の次数 $i-1$ の係数です。
  * `order  :: Int` 多項式の最大次数（次数）。

`Taylor1` 変数は呼び出し可能であることに注意してください。詳細については [`evaluate`](@ref) を参照してください。
