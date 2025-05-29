```
AbstractRegistrar(dict::Dict{String, Any}) → AbstractRegistrarの具象サブタイプ
```

辞書から新しいレジストラを作成します。この関数は、すべてのフィールドをキーワード引数として受け入れるコンストラクタを提供する`AbstractRegistrar`のサブタイプに使用できます。

レジストラの型は、`dict["_type"]`の値から解析されます。
