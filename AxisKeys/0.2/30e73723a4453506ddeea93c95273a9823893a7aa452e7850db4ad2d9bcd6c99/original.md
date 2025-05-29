```
wrapdims(table, value, names...; default=undef, sort=false, force=false)
```

Construct `KeyedArray(NamedDimsArray(A,names),keys)` from a `table` matching the [Tables.jl](https://github.com/JuliaData/Tables.jl) API. (It must support both `Tables.columns` and `Tables.rows`.)

The contents of the array is taken from the column `value::Symbol` of the table. Each symbol in `names` specifies a column whose unique entries become the keys along a dimenension of the array.

If there is no row in the table matching a possible set of keys, then this element of the array is undefined, unless you provide the `default` keyword. If several rows share the same set of keys, then by default an `ArgumentError` is thrown. Keyword `force=true` will instead cause these non-unique entries to be overwritten.

See also [`populate!`](@ref) to fill an existing array in the same manner.

Setting `AxisKeys.nameouter() = false` will reverse the order of wrappers produced.

# Examples

```jldoctest
julia> using DataFrames, AxisKeys

julia> df = DataFrame("a" => 1:3, "b" => 10:12.0, "c" => ["cat", "dog", "cat"])
3×3 DataFrame
 Row │ a      b        c      
     │ Int64  Float64  String 
─────┼────────────────────────
   1 │     1     10.0  cat
   2 │     2     11.0  dog
   3 │     3     12.0  cat

julia> wrapdims(df, :a, :b, :c; default=missing)
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   b ∈ 3-element Vector{Float64}
→   c ∈ 2-element Vector{String}
And data, 3×2 Matrix{Union{Missing, Int64}}:
         ("cat")    ("dog")
 (10.0)   1           missing
 (11.0)    missing   2
 (12.0)   3           missing

julia> wrapdims(df, :a, :b)
1-dimensional NamedDimsArray(KeyedArray(...)) with keys:
↓   b ∈ 3-element Vector{Float64}
And data, 3-element Vector{Union{Missing, Int64}}:
 (10.0)  1
 (11.0)  2
 (12.0)  3

julia> wrapdims(df, :a, :c)
ERROR: ArgumentError: Key ("cat",) is not unique

julia> wrapdims(df, :a, :c, force=true)
1-dimensional NamedDimsArray(KeyedArray(...)) with keys:
↓   c ∈ 2-element Vector{String}
And data, 2-element Vector{Int64}:
 ("cat")  3
 ("dog")  2
```
