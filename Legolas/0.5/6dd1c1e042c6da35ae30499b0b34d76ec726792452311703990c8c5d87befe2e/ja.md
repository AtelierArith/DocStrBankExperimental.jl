```
Legolas.SchemaVersion(name::AbstractString, version::Integer)
```

`Legolas.SchemaVersion{Symbol(name),version}()`を返します。

`name`が有効なスキーマ名でない場合、`ArgumentError`をスローします。

直接`Legolas.SchemaVersion{Symbol(name),version}()`を使用するよりも、このコンストラクタを使用することをお勧めします。
