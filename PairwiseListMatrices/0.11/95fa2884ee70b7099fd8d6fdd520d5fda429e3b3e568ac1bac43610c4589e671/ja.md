マクロ `@iteratelist` は `list` に対する `for` ループを生成しますが、ループ内で `getfield` 呼び出しを避けます。マクロの最初の引数は反復処理される `PairwiseListMatrix` で、2 番目の引数はループの本体です。本体内では `list` は `PairwiseListMatrix` のリストフィールドであり、`k` はそのリストに対するインデックスです。他の変数は現在のスコープで展開されます。`k` の値を変更してはいけません。

```jldoctest
julia> using PairwiseListMatrices

julia> PLM = PairwiseListMatrix([1,2,3], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2
 1  0  3
 2  3  0

julia> @iteratelist PLM println(list[k])
1
2
3

```
