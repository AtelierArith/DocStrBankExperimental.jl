```julia
lrmatmul(
    a::AbstractArray{Tv, 1},
    B::ExtendableSparse.ExtendableSparseMatrixCSC{Tv, Ti<:Integer},
    b::AbstractArray{Tv, 1};
    factor
) -> Any

```

ベクトル'-行列-ベクトル積 a'*B*b を計算します。
