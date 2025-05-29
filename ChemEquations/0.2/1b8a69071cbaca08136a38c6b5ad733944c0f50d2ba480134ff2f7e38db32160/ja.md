```julia
struct ChemEquation{T<:Real}
```

  * `tuples::Array{Tuple{ChemEquations.Compound, T}, 1} where T<:Real`

化学方程式の化合物とその係数を構造化された方法で保存します。
