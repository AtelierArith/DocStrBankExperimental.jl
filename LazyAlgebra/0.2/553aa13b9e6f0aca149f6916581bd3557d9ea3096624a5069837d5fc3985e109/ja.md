```
unveil(A)
```

は、マッピング `A` に埋め込まれたマッピングを明らかにします。もしそれが *装飾された* マッピングであれば（[`LazyAlgebra.DecoratedMapping`](@ref) を参照）、そうでなければ、単に *装飾された* マッピングでない場合は `A` を返します。

特別なケースとして、`A` は `LinearAlgebra.UniformScaling` のインスタンスであり、その結果は `A` に対応する LazyAlgebra マッピングです。
