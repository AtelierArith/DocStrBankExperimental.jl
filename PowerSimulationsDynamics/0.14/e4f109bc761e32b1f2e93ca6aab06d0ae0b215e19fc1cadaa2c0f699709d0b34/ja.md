```
get_state_series(
    res::SimulationResults,
    ref::Tuple{String, Symbol};
    dt::Union{Nothing, Float64, Vector{Float64}} = nothing
)
end
```

DAEソリューションから状態の系列を取得するための関数。

# 引数

  * `res::SimulationResults` : ソリューションを含むシミュレーション結果オブジェクト
  * `ref:Tuple{String, Symbol}` : 名前としての`String`と関連する状態としての`Symbol`を介して動的デバイスを識別するために使用されるタプル。
