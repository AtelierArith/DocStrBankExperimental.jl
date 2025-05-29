```
set_data_dimension!(domain::Domain, dim::NamedDimension [, coordinates], ; allow_exists=false)
```

[`NamedDimension`](@ref)としてドメインデータ次元を定義し、オプションで座標名のベクトルを添付します。

変数は、その`:data_dims`変数属性を使用して、名前のリストとしてデータ次元を指定できます。
