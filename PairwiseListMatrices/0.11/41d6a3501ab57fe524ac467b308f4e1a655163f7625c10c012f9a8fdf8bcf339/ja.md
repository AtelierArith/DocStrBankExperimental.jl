`apply2diag` 関数は、最初の引数である関数 `fun` を `PairwiseListMatrix{T,false,VT}` の `diag` フィールドの各要素に適用しますが、ループ内で `getfield` 呼び出しを避けます。マクロの第二引数は、反復処理される `PairwiseListMatrix` です。`fun` は二つの引数を取る必要があります; 最初は `PairwiseListMatrix` の `diag` フィールドで、二つ目は与えられた反復での対角要素のベクトルに対するインデックスです。

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([1,2,3], false)
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 0  1  2
 1  0  3
 2  3  0

julia> apply2diag((diag, k) -> diag[k] += 10k, plm)

julia> plm
3×3 PairwiseListMatrix{Int64,false,Array{Int64,1}}:
 10   1   2
  1  20   3
  2   3  30

```
