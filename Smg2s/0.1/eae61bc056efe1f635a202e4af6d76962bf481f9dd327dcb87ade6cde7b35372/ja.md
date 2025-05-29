```
Nilp(matrix::SparseMatrixCSC{Tv, Ti} ,size::Ti; maxdegree::Ti=80) where{Tv <: Real, Ti <: Integer}
```

ユーザーが提供したスパース行列 `matrix` から次元が `size` のニルポテント行列を作成します。この行列はニルポテントであり、そのニルポテント性は `80` を超えてはいけません。生成前に、SMG2S.jl はユーザーが提供した行列がニルポテント行列であり、ニルポテント性が `80` を超えていないかを確認します。どちらかの条件を満たさない場合、エラーメッセージが表示されます。

## 例

```jldoctest; setup = :(using SMG2S; using SparseArrays)
julia> nilpMatrix = sparse([0. 1 1 0; 0 0 1 1 ; 0 0 0 1 ; 0 0 0 0])
4×4 SparseMatrixCSC{Float64, Int64} with 5 stored entries:
  ⋅   1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅

julia> SMG2S.Nilp(nilpMatrix,4)
┌ Info: 与えられたニルポテント行列の次数は:
└   degree = 4
Nilpotent{Int64}(1, 4, 4,
  ⋅   1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅ )
```

## 例

```julia
julia> nilpMatrix = sparse([1. 1 1 0; 0 0 1 1 ; 0 0 0 1 ; 0 0 0 0])
4×4 SparseMatrixCSC{Float64, Int64} with 6 stored entries:
 1.0  1.0  1.0   ⋅
  ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅   1.0
  ⋅    ⋅    ⋅    ⋅

julia> SMG2S.Nilp(nilpMatrix,4)
ERROR: 与えられたニルポテント行列は無効です
```
