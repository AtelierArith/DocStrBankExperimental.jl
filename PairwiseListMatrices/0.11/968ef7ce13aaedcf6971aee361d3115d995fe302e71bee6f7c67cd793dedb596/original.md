It takes a `PairwiseListMatrix` and converts it to a `Dict` of `Symbol`s to arrays. The returned dictionary can be easily converted into a `DataFrame`.

```jldoctest
julia> using PairwiseListMatrices, DataFrames

julia> nplm = setlabels(PairwiseListMatrix([10,20,30], false), ["a","b","c"])
3×3 Named PairwiseListMatrix{Int64,false,Array{Int64,1}}
A ╲ B │  a   b   c
──────┼───────────
a     │  0  10  20
b     │ 10   0  30
c     │ 20  30   0

julia> dict = to_dict(nplm, diagonal=false)
Dict{Symbol,Array{T,1} where T} with 3 entries:
  :values => [10, 20, 30]
  :j      => ["b", "c", "c"]
  :i      => ["a", "a", "b"]

julia> DataFrame(dict)
3×3 DataFrames.DataFrame
│ Row │ i      │ j      │ values │
│     │ String │ String │ Int64  │
├─────┼────────┼────────┼────────┤
│ 1   │ a      │ b      │ 10     │
│ 2   │ a      │ c      │ 20     │
│ 3   │ b      │ c      │ 30     │
```
