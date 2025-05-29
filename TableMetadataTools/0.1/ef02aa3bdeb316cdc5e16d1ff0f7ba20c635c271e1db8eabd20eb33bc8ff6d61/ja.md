```
toml2meta!(table, toml::Union{AbstractString, IO})
```

`toml`で表されるテーブルレベルおよびカラムレベルのメタデータを`table`に格納します（以前に存在していたメタデータはすべて破棄されます）。

この関数は、`toml`が適切にフォーマットされたTOMLであると仮定します。通常、[`meta2toml`](@ref)によって以前に生成されたものです。

参照: [`meta2toml`](@ref)
