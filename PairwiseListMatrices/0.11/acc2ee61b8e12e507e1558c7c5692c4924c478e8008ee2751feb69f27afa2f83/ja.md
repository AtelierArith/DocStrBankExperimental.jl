マクロ `@iterateupper` は、最初の引数として与えられた `PairwiseListMatrix` の上三角部分を反復処理します。2番目の引数は、対角線を反復処理に含める必要がある場合は `true`、そうでない場合は `false` にする必要があります。最後の引数はループの本体であり、ここで `list` は `PairwiseListMatrix` のリストおよび対角線のフィールドで、`k` はその `list` に対するインデックスです。また、上三角部分の行列内のその位置 `k` に対して、対応する `i` および `j` インデックスを使用することもできます。他の変数は現在のスコープで展開されます。`i`、`j` または `k` の値を変更してはいけません。

```jldoctest
julia> using PairwiseListMatrices

julia> PLM = PairwiseListMatrix([1,2,3], true)
2×2 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 1  2
 2  3

julia> mat = zeros(Int, 2, 2)
2×2 Array{Int64,2}:
 0  0
 0  0

julia> let mat = mat # To avoid using global
           @iterateupper PLM true mat[i,j] = list[k]
       end

julia> mat
2×2 Array{Int64,2}:
 1  2
 0  3

```
