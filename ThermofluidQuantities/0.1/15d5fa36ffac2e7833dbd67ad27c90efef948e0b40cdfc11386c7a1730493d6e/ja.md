```
value(a::PhysicalQuantity,units::Unitful.Units)
```

`a`の数値を、`units`に変換して返します。`units`の形式は`Unitful`形式でなければならず、例えば`u"Pa"`のように、`a`と次元的に互換性がある必要があります。
