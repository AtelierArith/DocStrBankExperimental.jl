```julia
assemble_massmatrix(
    E::SparseArrays.SparseMatrixCSC{Float64, Int64},
    w::AbstractVector{Float64}
) -> SparseArrays.SparseMatrixCSC{Float64, Int64}

```

与えられたローカル積分次数に対する質量行列をメッシュのすべての要素とqdimコンポーネントに対して返します。

既存の基底行列Eと重みベクトルwを引数として受け取ります。Eがすでに存在する場合、直接アセンブリと比較してパフォーマンスの利点をもたらす可能性があります。Eとwのコンポーネント数と数値積分次数は一致する必要があることに注意してください。
