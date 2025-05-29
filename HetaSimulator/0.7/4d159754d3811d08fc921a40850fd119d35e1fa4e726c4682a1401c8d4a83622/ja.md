```
fit(platform::Platform,
  parameters_fitted;
  scenarios::Union{AbstractVector{Symbol}, Nothing} = nothing,
  kwargs...
) where C<:AbstractScenario
```

実験測定にフィットするパラメータ。`FitResult`型を返します。

例:

`fit(platform, [:k1=>0.1,:k2=>0.2,:k3=>0.3];scenarios=[:scn2,:scn3])`

引数:

  * `platform` : [`Platform`](@ref)型のプラットフォーム
  * `parameters_fitted` : 最適化パラメータとその初期値
  * `scenarios` : `Symbol`型のシナリオ識別子のベクター。デフォルトは`nothing`
  * `kwargs...` : `fit(scenario_pairs::Vector{<:Pair}, parameters_fitted::Vector{<:Pair}`でサポートされる他のODEソルバーおよび`fit`関連の引数
