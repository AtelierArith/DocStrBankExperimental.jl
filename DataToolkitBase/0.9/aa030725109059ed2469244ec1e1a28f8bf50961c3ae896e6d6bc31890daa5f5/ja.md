```
fromspec(ADT::Type{<:AbstractDataTransformer}, dataset::DataSet, spec::Dict{String, Any})
```

`spec`に従って`dataset`の`ADT`を作成します。

`ADT`は、型パラメータとしてドライバ名を含むか、`spec`の`"driver"`キーから読み取られます。
