```
struct VectorizedHermitianMatrix{T} <: AbstractMatrix{Complex{T}}
    Q::Vector{T}
    n::Int
end
```

エルミート $n \times n$ 行列は、行列のベクトル化された上三角実部を `Q` ベクトルに格納し、その後にベクトル化された上三角虚部を格納します（これは `ComplexOptInterface.HermitianPositiveSemidefiniteConeTriangle` のベクトル化された形式に対応します）。これは `setindex!` を除く `AbstractMatrix` インターフェースを実装しています。なぜなら、それが対称性を壊す可能性があるからです。代わりに [`symmetric_setindex!`](@ref) 関数を使用する必要があります。
