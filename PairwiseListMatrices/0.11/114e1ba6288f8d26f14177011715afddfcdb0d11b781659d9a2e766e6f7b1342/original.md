This function join two PairwiseListMatrices by their labels, returning two PairwiseListMatrices with same size and labels. There are 4 `kind`s of joins:

  * `:inner` : Intersect. The output matrices only include the labels that are in both PairwiseListMatrices
  * `:outer` : Union. Include the labels of the two PairwiseListMatrices.
  * `:left` : Only use labels from the first argument.
  * `:right` : Only use labels from the second argument.

`NaN`s are filled in where needed to complete joins. The default value for missing values can be changed passing a tuple to `missing`.

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
