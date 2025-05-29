```
assemble_laplacian(
    D::SparseMatrixCSC{Float64, Int64},
    w::AbstractVector{Float64}
) -> SparseMatrixCSC{Float64, Int64}
```

メッシュのすべての要素と qdim コンポーネントのラプラス剛性行列を返します。

既存の導関数行列 D と重みベクトル w を引数として受け取ります。D がすでに存在する場合、直接アセンブリと比較してパフォーマンスの利点をもたらす可能性があります。D と w のコンポーネント数および数値積分の次数は一致する必要があることに注意してください。
