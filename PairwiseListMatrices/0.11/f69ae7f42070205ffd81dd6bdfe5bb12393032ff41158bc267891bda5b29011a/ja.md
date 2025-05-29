マクロ `@iteratediag` は `PairwiseListMatrix{T,false,VT}` の `diag` フィールドに対して `for` ループを書きますが、ループ内で `getfield` の呼び出しを避けます。マクロの最初の引数は反復処理される `PairwiseListMatrix` で、2番目はループの本体です。本体内では `diag` は `PairwiseListMatrix` の `diag` フィールドであり、`k` はそのベクターに対するインデックスです。他の変数は現在のスコープで展開されます。`k` の値を変更してはいけません。

```jldoctest
julia> using PairwiseListMatrices

julia> PLM = PairwiseListMatrix([1,2,3], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2
 1  0  3
 2  3  0

julia> @iteratediag PLM diag[k] += 10k

julia> PLM
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 10   1   2
  1  20   3
  2   3  30

```
