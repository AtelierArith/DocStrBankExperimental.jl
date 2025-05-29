`Matrix`、`DataFrame`、または類似の構造からの `PairwiseListMatrix` の作成。デフォルトでは、i（遅い）および j（速い）のラベルを持つ列はそれぞれ 1 と 2 です。値はデフォルトで列 3 から取得されます。

```jldoctest
julia> using PairwiseListMatrices, Pkg, DelimitedFiles

julia> import PairwiseListMatrices

julia> filename = joinpath(dirname(pathof(PairwiseListMatrices)), "..", "test", "example.csv");

julia> dat = readdlm(filename, ',')
3×3 Array{Any,2}:
 "A"  "B"  10
 "A"  "C"  20
 "B"  "C"  30

julia> from_table(dat, false)
3×3 Named PairwiseListMatrix{Any,false,Array{Any,1}}
A ╲ B │       A        B        C
──────┼──────────────────────────
A     │ nothing       10       20
B     │      10  nothing       30
C     │      20       30  nothing
```

これは `DataFrame` から `PairwiseListMatrix` を作成するのにも便利です：

```
julia> using PairwiseListMatrices, DataFrames, CSV, Pkg

julia> import PairwiseListMatrices

julia> filename = joinpath(dirname(pathof(PairwiseListMatrices)), "..", "test", "example.csv");

julia> df = CSV.read(filename, header=false)
3×3 DataFrames.DataFrame
│ Row │ Column1 │ Column2 │ Column3 │
│     │ String⍰ │ String⍰ │ Int64⍰  │
├─────┼─────────┼─────────┼─────────┤
│ 1   │ A       │ B       │ 10      │
│ 2   │ A       │ C       │ 20      │
│ 3   │ B       │ C       │ 30      │

julia> from_table(df, false)
3×3 Named PairwiseListMatrix{Union{Missing, Int64},false,Array{Union{Missing, Int64},1}}
A ╲ B │       A        B        C
──────┼──────────────────────────
A     │ missing       10       20
B     │      10  missing       30
C     │      20       30  missing
```
