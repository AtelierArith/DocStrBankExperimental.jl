```
ustrip(a::PhysicalQuantity,units::Unitful.Units)
```

`a`の数値を返し、`units`に変換し、単位を取り除きます。`units`の形式は`Unitful`形式でなければならず、例えば`u"Pa"`のように、`a`と次元的に互換性がある必要があります。
