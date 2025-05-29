この関数は、2つのPairwiseListMatricesをラベルで結合し、同じサイズとラベルの2つのPairwiseListMatricesを返します。結合には4つの`kind`があります：

  * `:inner` : 積集合。出力行列には、両方のPairwiseListMatricesに存在するラベルのみが含まれます。
  * `:outer` : 和集合。2つのPairwiseListMatricesのラベルを含めます。
  * `:left` : 最初の引数のラベルのみを使用します。
  * `:right` : 2番目の引数のラベルのみを使用します。

`NaN`は、結合を完了するために必要な場所に埋め込まれます。欠損値のデフォルト値は、`missing`にタプルを渡すことで変更できます。

```jldoctest
julia> using PairwiseListMatrices

julia> l = setlabels(PairwiseListMatrix([1.,2.,3.], false), ["a","b","c"]) # a b c
3×3 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   a    b    c
──────┼──────────────
a     │ 0.0  1.0  2.0
b     │ 1.0  0.0  3.0
c     │ 2.0  3.0  0.0

julia> r = setlabels(PairwiseListMatrix([1.,2.,3.], false), ["b","c","d"]) # b c d
3×3 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   b    c    d
──────┼──────────────
b     │ 0.0  1.0  2.0
c     │ 1.0  0.0  3.0
d     │ 2.0  3.0  0.0

julia> join(l, r, kind=:inner) # b c
(2×2 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   b    c
──────┼─────────
b     │ 0.0  3.0
c     │ 3.0  0.0, 2×2 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   b    c
──────┼─────────
b     │ 0.0  1.0
c     │ 1.0  0.0)

julia> join(l, r, kind=:outer) # a b c d
(4×4 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   a    b    c    d
──────┼───────────────────
a     │ 0.0  1.0  2.0  NaN
b     │ 1.0  0.0  3.0  NaN
c     │ 2.0  3.0  0.0  NaN
d     │ NaN  NaN  NaN  NaN, 4×4 Named PairwiseListMatrix{Float64,false,Array{Float64,1}}
A ╲ B │   a    b    c    d
──────┼───────────────────
a     │ NaN  NaN  NaN  NaN
b     │ NaN  0.0  1.0  2.0
c     │ NaN  1.0  0.0  3.0
d     │ NaN  2.0  3.0  0.0)

```
