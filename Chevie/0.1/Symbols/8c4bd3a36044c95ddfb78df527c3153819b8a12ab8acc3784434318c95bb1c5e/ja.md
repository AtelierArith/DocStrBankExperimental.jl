`BDSymbols(n,d)`

は、欠陥 `d` と階数 `n` の 2-シンボルを返します（Weyl 型 B,C,D,2D 用）。もし `d==0` の場合、等しいエントリを持つシンボルが 2 回返され、最初のエントリ、繰り返し因子 2、および序数 0 または 1 で表されます。したがって、`BDSymbols(n, 0)` は Weyl 群の型 `Dₙ` のキャラクターのためのパラメータのセットです。

```julia-repl
julia> BDSymbols(2,1)
5-element Vector{Vector{Vector{Int64}}}:
 [[1, 2], [0]]
 [[0, 2], [1]]
 [[0, 1, 2], [1, 2]]
 [[2], []]
 [[0, 1], [2]]

julia> BDSymbols(4,0)
13-element Vector{Vector}:
 Any[[1, 2], 2, 0]
 Any[[1, 2], 2, 1]
 [[0, 1, 3], [1, 2, 3]]
 [[0, 1, 2, 3], [1, 2, 3, 4]]
 [[1, 2], [0, 3]]
 [[0, 2], [1, 3]]
 [[0, 1, 2], [1, 2, 4]]
 Any[[2], 2, 0]
 Any[[2], 2, 1]
 [[0, 1], [2, 3]]
 [[1], [3]]
 [[0, 1], [1, 4]]
 [[0], [4]]
```
