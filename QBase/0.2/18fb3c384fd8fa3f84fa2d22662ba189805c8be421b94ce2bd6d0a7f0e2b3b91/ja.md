```
n_choose_k_matrices( n :: Int64, k :: Int64 ) :: Vector{Matrix{Bool}}
```

`n` 行 `k` 列の行列のセットを生成し、`n` 行から `k` 列を選択するすべての組み合わせを表します。各列には単一の非ゼロ要素が含まれ、`k` 行には非ゼロ要素が含まれます。

例：

```jldoctest
julia> n_choose_k_matrices( 4, 2 )
6-element Array{Array{Bool,2},1}:
 [1 0; 0 1; 0 0; 0 0]
 [1 0; 0 0; 0 1; 0 0]
 [1 0; 0 0; 0 0; 0 1]
 [0 0; 1 0; 0 1; 0 0]
 [0 0; 1 0; 0 0; 0 1]
 [0 0; 0 0; 1 0; 0 1]
```

`n ≥ k ≥ 1` が満たされない場合、`DomainError` がスローされます。
