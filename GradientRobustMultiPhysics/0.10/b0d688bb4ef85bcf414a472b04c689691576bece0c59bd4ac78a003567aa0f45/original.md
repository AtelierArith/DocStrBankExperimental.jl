```julia
lrmatmul(
    a::AbstractArray{Tv, 1},
    B::ExtendableSparse.ExtendableSparseMatrix{Tv, Ti<:Integer},
    b::AbstractArray{Tv, 1};
    factor
) -> Any

```

Computes vector'-matrix-vector product a'*B*b.
