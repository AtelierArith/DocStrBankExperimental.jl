```julia
isoval2filling(
    flat::Crystalline.AbstractFourierLattice{D},
    isoval::Real
) -> Any
isoval2filling(
    flat::Crystalline.AbstractFourierLattice{D},
    isoval::Real,
    nsamples::Integer
) -> Any

```

`flat`によって定義された等値面の内部の充填率を、等値値`isoval`に対して返します。

キーワード引数`nsamples`は、この答えを評価する際に使用されるグリッド解像度を指定します（階段積分を使用）。
