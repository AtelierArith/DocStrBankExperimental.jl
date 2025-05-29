```
InterpretMe.partial_dependence(data::Array{<:Any,2},
                               features::Union{<:Integer,Vector{<:Integer}},
                               estimate_fn, grid_size::Int,
                               return_ice::Bool)
```

機械学習モデルの部分依存を計算します。

`estimate_fn` は、入力の行列から予測のベクトルを生成するモデルの関数です。 `feature_names` は、`data` の特徴に対応する特徴名である必要があります。 `return_ice` はICEラインを返すかどうかを示します。戻り値は `pd` 部分依存の結果、`grid_values` は選択されたすべての特徴のグリッド値です。
