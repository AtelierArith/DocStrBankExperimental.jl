`basis_at(basis, x)`

Return an iterable with known element type and length (`Base.HasEltype()`, `Base.HasLength()`) of basis functions in `basis` evaluated at `x`.

Univariate bases operate on real numbers, while for multivariate bases, `Tuple`s or `StaticArrays.SVector` are preferred for performance, though all `<:AbstractVector` types should work.

Methods are type stable.

!!! note
    Consequences are undefined when evaluating outside the domain.

