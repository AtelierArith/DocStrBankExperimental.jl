```
set_param!(md::ModelDef, comp_def::AbstractComponentDef, param_name::Symbol, 
            model_param_name::Symbol, value; dims=nothing)
```

コンポーネント `comp_def` のパラメータ `param_name` をモデル定義 `md` の値 `value` に設定します。これにより、名前 `model_param_name` の共有モデルパラメータが作成され、`comp_name` のパラメータ `param_name` がそれに接続されます。

`value` はスカラー、配列、または NamedArray である可能性があります。オプションのキーワード引数 'dims' は提供されたデータの次元名のリストであり、モデルのインデックスラベルと一致するかどうかを確認するために使用されます。
