```
set_param!(m::Model, comp_name::Symbol, param_name::Symbol, value; dims=nothing)
```

モデル `m` のコンポーネント `comp_name` のパラメータを指定された `value` に設定します。`value` はスカラー、配列、または NamedArray であることができます。オプションのキーワード引数 'dims' は提供されたデータの次元名のリストであり、モデルのインデックスラベルと一致するかどうかを確認するために使用されます。
