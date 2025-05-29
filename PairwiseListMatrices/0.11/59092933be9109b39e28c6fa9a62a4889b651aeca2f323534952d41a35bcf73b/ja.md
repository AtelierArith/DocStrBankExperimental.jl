`nelements`の行列から`i`と`j`のインデックスを使って`list`の`k`インデックスを返します。`i<j`である必要があります。`diagonal`は、対角値が`list`に含まれている場合は`true`または`Val{true}`である必要があります。`i>j`で使用してはいけません。

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([10,20,30,40,50,60], true)
3×3 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 10  20  30
 20  40  50
 30  50  60

julia> ij2k(1, 2, 3, true)
2

julia> getlist(plm)[2]
20

```
