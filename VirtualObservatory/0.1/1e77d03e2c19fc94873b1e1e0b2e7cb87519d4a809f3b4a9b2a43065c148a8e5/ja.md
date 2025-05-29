```
execute([restype=StructArray], tap::TAPService, query::AbstractString; kwargs...)
```

指定されたTAPサービスでADQL `query`を実行し、結果を`StructArray`として返します - 完全な機能を持つJuliaテーブルです。

`kwargs`は`VOTables.read`に渡されます。たとえば、`unitful=true`を指定して、単位を持つ列を`Unitful.jl`の値に解析します。
