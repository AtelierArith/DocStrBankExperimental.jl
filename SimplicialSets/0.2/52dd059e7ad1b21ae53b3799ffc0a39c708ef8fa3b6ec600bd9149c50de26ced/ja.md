```
diag(x::T) where T <: AbstractSimplex -> ProductSimplex{Tuple{T,T}}
```

`x`の対角マップに基づく画像を返します。これは、`x`を含む単体集合から自身とのデカルト積へのマップです。

この関数は線形であり、キーワード引数`coefftype`、`addto`、`coeff`、`sizehint`、および`is_filtered`をサポートしています。これらはマクロ`@linear`で説明されています。

関連情報として[`coprod`](@ref)、`LinearCombinations.@linear`を参照してください。
