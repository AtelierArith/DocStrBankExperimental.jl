`diagblocks(M::Matrix)`

`M` は正方行列である必要があります。頂点 `1:size(M,1)` を持つグラフ `G` を定義し、`M[i,j]` または `M[j,i]` がゼロまたは `false` でない場合に `i` と `j` の間にエッジを持ちます。`diagblocks` はベクトルのベクトル `I` を返し、`I[1]`、`I[2]` などは `G` の各連結成分の頂点です。言い換えれば、`M[I[1],I[1]]`、`M[I[2],I[2]]` などは `M` の対角ブロックです。

```julia-repl
julia> m=[0 0 0 1;0 0 1 0;0 1 0 0;1 0 0 0]
4×4 Matrix{Int64}:
 0  0  0  1
 0  0  1  0
 0  1  0  0
 1  0  0  0

julia> diagblocks(m)
2-element Vector{Vector{Int64}}:
 [1, 4]
 [2, 3]

julia> m[[1,4,2,3],[1,4,2,3]]
4×4 Matrix{Int64}:
 0  1  0  0
 1  0  0  0
 0  0  0  1
 0  0  1  0
```
