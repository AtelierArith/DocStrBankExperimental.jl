```
struct SymMatrix{T} <: AbstractMatrix{T}
    Q::Vector{T}
    n::Int
end
```

対称 $n \times n$ 行列は、行列の上三角部分をベクトル化したものを `Q` ベクトルに格納します（これは `MathOptInterface.PositiveSemidefiniteConeTriangle` のベクトル化された形式に対応します）。これは `setindex!` を除く `AbstractMatrix` インターフェースを実装しています。なぜなら、それが対称性を壊す可能性があるからです。代わりに [`symmetric_setindex!`](@ref) 関数を使用する必要があります。
