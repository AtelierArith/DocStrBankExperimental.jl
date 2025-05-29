```
set_param!(m::Model, comp_name::Symbol, param_name::Symbol, model_param_name::Symbol, value; dims=nothing)
```

モデル `m` のコンポーネント `comp_name` のパラメータ `param_name` を指定された `value` に設定し、提供された名前 `model_param_name` でモデルのパラメータリストに値を格納します。`value` はスカラー、配列、または NamedArray である可能性があります。オプションのキーワード引数 'dims' は提供されたデータの次元名のリストであり、モデルのインデックスラベルと一致するかどうかを確認するために使用されます。
