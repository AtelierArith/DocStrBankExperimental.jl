```julia
assemble_massmatrix_boundary(
    E::SparseArrays.SparseMatrixCSC{Float64, Int64},
    w::AbstractVector{Float64}
) -> SparseArrays.SparseMatrixCSC{Float64, Int64}

```

与えられた局所積分次数に対して、メッシュのすべてまたは指定された境界要素の質量行列と画像次元 qdim コンポーネントを返します。

既存の境界基底行列 E と重みベクトル w を引数として受け取ります。E がすでに存在する場合、直接アセンブリと比較してパフォーマンスの利点をもたらす可能性があります。E と w のコンポーネント数および数値積分次数は一致する必要があることに注意してください。
