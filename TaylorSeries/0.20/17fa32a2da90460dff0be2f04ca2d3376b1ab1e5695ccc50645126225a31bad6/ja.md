```
HomogeneousPolynomial{T<:Number} <: AbstractSeries{T}
```

多くの（>1）独立変数における同次多項式のデータ型。

**フィールド:**

  * `coeffs  :: Array{T,1}` 同次多項式の展開係数；$i$-番目の成分は単項式に関連しており、独立変数の次数は `coeff_table[order+1][i]` によって指定されます。
  * `order   :: Int` 同次多項式の次数（度）。

`HomogeneousPolynomial` 変数は呼び出し可能であることに注意してください。詳細については [`evaluate`](@ref) を参照してください。
