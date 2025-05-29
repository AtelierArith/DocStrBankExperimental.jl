```
add_shared_param!(m::Model, name::Symbol, value::Any; dims::Array{Symbol}=Symbol[], datatype::DataType=Nothing)
```

モデル `m` に名前 `name` と値 `value` を持つ共有パラメータを追加するユーザー向けAPI関数であり、次元名の配列 `dims` はデフォルトで空のベクターになります。追加されたモデルパラメータの `is_shared` 属性は `true` になります。

`value` はスカラー、配列、または NamedArray である可能性があります。オプションのキーワード引数 'dims' は提供されたデータの次元名のリストであり、モデルのインデックスラベルと一致するかどうかを確認するために使用されます。`value` がスカラーでない場合はこれを含める必要があり、デフォルトは空のベクターです。オプションのキーワード引数 `datatype` は、共有モデルパラメータに使用するデータ型を指定するためにユーザーが使用できます。
