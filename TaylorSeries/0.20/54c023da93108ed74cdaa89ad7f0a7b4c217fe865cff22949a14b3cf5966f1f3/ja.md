```
TaylorN{T<:Number} <: AbstractSeries{T}
```

多くの（>1）独立変数における多項式展開のデータ型。

**フィールド:**

  * `coeffs  :: Array{HomogeneousPolynomial{T},1}` `HomogeneousPolynomial` エントリを含むベクトル。$i$ 番目の成分は、次数 $i-1$ の同次多項式に対応します。
  * `order   :: Int`  多項式展開の最大次数。

`TaylorN` 変数は呼び出し可能であることに注意してください。詳細については、[`evaluate`](@ref)を参照してください。
