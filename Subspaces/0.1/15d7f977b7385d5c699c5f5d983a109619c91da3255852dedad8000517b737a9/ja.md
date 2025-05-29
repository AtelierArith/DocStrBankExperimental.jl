```julia
each_basis_element(
    S::Subspaces.Subspace
) -> Slices{P, _A, AX, T, 1} where {P<:Array, _A, AX<:Tuple{Any}, T}

```

部分空間の直交基底ベクトルを反復するジェネレーターを作成します。
