```
OneHotEncoder(Dict(
   # 名義列
   :nominal_columns => Int[],

   # 名義列の値マップ。キーは列インデックス、値はその列の
   # 可能な値のリストです。
   :nominal_column_values_map => Dict{Int,Any}()
))
```

名義特徴を持つmyinstancesをワンホット形式に変換し、インスタンス行列を要素型Float64に強制します。

`fit!`と`transform`を実装します。
