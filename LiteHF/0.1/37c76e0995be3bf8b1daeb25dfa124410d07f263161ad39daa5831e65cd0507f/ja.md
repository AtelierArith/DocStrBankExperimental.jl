```
struct PyHFModel{E, O, P} <: AbstractModel
    expected::E
    observed::O
    priors::P
    prior_names
    inits::Vector{Float64}
end
```

[build_pyhf](@ref) からの結果を保持するための構造体です。アクセサ関数のリストは次のとおりです。

  * expected(p::PyHFModel)
  * observed(p::PyHFModel)
  * priors(p::PyHFModel)
  * prior_names(p::PyHFModel)
  * inits(p::PyHFModel)
