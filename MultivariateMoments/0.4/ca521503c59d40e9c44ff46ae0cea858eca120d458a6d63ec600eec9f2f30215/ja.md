```
mutable struct MomentMatrix{T, B<:MultivariateBases.AbstractPolynomialBasis, MT<:AbstractMatrix{T}} <: AbstractMeasureLike{T}
    Q::MT
    basis::B
    support::Union{Nothing, AlgebraicSet}
end
```

測度 $\nu$ は、対称行列 `Q` におけるモーメント行列 $x x^\top$ のモーメントによって表されます。$\mathbb{E}_{\nu}[p] = 0$ となるすべての多項式 $p$ のゼロである点の集合は、計算されたときにフィールド `support` に格納されます。
