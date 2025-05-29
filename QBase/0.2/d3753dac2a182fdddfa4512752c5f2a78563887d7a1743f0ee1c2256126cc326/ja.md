```
stirling2_matrices( n :: Int64, k :: Int64 ) :: Vector{Matrix{Bool}}
```

`k` 行 `n` 列の行列の集合を生成します。行はグループに対応し、列はグループ化された要素です。非ゼロの要素は、列の ID が対応する行にグループ化されていることを示します。

例：

```jldoctest
julia> stirling2_matrices( 4, 2 )
7-element Array{Array{Bool,2},1}:
 [1 1 1 0; 0 0 0 1]
 [0 0 1 0; 1 1 0 1]
 [1 1 0 0; 0 0 1 1]
 [1 0 1 0; 0 1 0 1]
 [0 1 0 0; 1 0 1 1]
 [0 1 1 0; 1 0 0 1]
 [1 0 0 0; 0 1 1 1]
```

`n ≥ k ≥ 1` が満たされない場合、`DomainError` がスローされます。
