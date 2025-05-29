```
@enumbatteries T [options]
```

Enum型 `T` のためにいくつかのメソッドを自動的に導出します。

# 例

```julia
@enum Color Red Blue Yellow
@enumbatteries Color
@enumbatteries Color hash=false # `Base.hash` をオーバーロードしない
@enumbatteries Color symbol_conversion=true # convert(Color, :Blue), Color(:Blue), convert(Symbol, Blue), Symbol(Blue) を許可
```

サポートされているオプションとデフォルトは次のとおりです：

  * **string_conversion** = false:

`convert(MyEnum, ::String)`, `MyEnum(::String)`, `convert(String, ::MyEnum)` および `String(::MyEnum)` を追加します。

  * **symbol_conversion** = false:

`convert(MyEnum, ::Symbol)`, `MyEnum(::Symbol)`, `convert(Symbol, ::MyEnum)` および `Symbol(::MyEnum)` を追加します。

  * **selfconstructor** = true:

`T(self::T) = self` の形式のコンストラクタを追加します。

  * **hash** = false:

構造的に `Base.hash` を定義します。

  * **typesalt** = nothing:

`hash=true` の場合にのみ使用されます。この場合、`hash` は `typesalt` と `hash_eq_as(obj)` から純粋に計算されます。型 `T` はそれ以外では使用されません。これにより、異なるマシンやJuliaのバージョンで実行する際にハッシュが一定に保たれる可能性が高くなります。
