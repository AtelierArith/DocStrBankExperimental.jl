```
sim(platform::Platform; 
  scenarios::Union{AbstractVector{Symbol}, AbstractVector{InvertedIndex{Symbol}}, Nothing} = nothing,
  kwargs...) where {C<:AbstractScenario}
```

プラットフォームに含まれるシナリオをシミュレートします。`Vector{Pair}`を返します。

例: `sim(platform)`

引数:

  * `platform` : [`Platform`](@ref) 型のプラットフォーム
  * `scenarios` : プラットフォームに含まれるシナリオの名前を含む `Vector`。デフォルト値 `nothing` はプラットフォーム内のすべてのシナリオを表します
  * `kwargs...` : `sim(scenario_pairs::Vector{Pair})` でサポートされている他のキーワード引数
