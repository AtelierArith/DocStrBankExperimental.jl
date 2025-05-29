```
dimensionalize(f, args::AbstractQuantity...)
```

すべての引数を基本単位に変換し、値と次元に `f` を適用し、可能な限り狭い量を返します。量に対して新しい関数を定義するのに便利です。

したがって、量に対して `f` をサポートするには、単に次のように定義します。

f(dims::AbstractDimensions...) f(args::AbstractQuantity...) = dimensionalize(f, args...)
