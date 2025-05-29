```
TropicalPuiseuxPoly(coeff::Dict, exp::Vector{Vector{T}}, sorted::Bool)
```

係数のベクトルと指数のベクトルから熱帯プイセウス多項式を構築します。まず、指数を辞書順にソートし、その後係数の辞書を構築します。

```jldoctest
julia> f = TropicalPuiseuxPoly([1, 2], [[1, 2], [2, 1]])
  TropicalPuiseuxPoly{Int64}(Dict([2, 1] => 2, [1, 2] => 1), [[1, 2], [2, 1]])
```
