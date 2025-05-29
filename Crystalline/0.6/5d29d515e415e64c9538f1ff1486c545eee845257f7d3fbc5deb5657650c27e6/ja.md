```julia
filling2isoval(
    flat::Crystalline.AbstractFourierLattice{D}
) -> Any
filling2isoval(
    flat::Crystalline.AbstractFourierLattice{D},
    filling::Real
) -> Any
filling2isoval(
    flat::Crystalline.AbstractFourierLattice{D},
    filling::Real,
    nsamples::Integer
) -> Any

```

`flat`のisovalueを返します。これにより、定義されたレベルセットのisosurfaceの内部が単位セルの`filling`の割合を囲むようになります。

キーワード引数`nsamples`は、この答えを評価する際に使用されるグリッド解像度を指定します（Statistics.jlの`quantile`を介して）。
