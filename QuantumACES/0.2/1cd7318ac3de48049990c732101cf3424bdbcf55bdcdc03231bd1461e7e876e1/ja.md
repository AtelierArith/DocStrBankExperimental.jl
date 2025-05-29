```
get_layer_times(layer_types::Vector{Symbol}, layer_time_dict::Dict{Symbol, Float64})
```

回路内の各レイヤーを実装するのにかかる時間を、`layer_types`内のタイプに基づいて、`layer_time_dict`に指定された時間を含めて、最終的な測定とリセットの時間も含めて返します。
