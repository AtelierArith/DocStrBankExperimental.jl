```
SmallCollections.default(::Type{T}) where T -> T
SmallCollections.default(::T) where T -> T
```

`AbstractSmallVector`の未使用要素を埋めるために使用される型`T`のデフォルト値を返します。これは、`T`が代数演算をサポートしている場合は`zero(T)`として定義する必要があります。それ以外の場合は、型`T`の任意の値で構いません。

この関数は、数値型、ビット型、`Symbol`、`AbstractChar`、`AbstractString`、`Tuple`、`NamedTuple`、`AbstractFixedVector`、`AbstractSmallVector`および`SmallBitSet`のメソッドを持っています。他の型のメソッドは明示的に定義する必要があります。

`Base.isbitstype`も参照してください。
