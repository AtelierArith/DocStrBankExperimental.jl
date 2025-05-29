```
groupby(d::AbstractDataFrame, cols;
        sort::Union{Bool, Nothing, NamedTuple}=nothing,
        skipmissing::Bool=false)
```

Return a `GroupedDataFrame` representing a view of an `AbstractDataFrame` split into row groups.

# Arguments

  * `df` : an `AbstractDataFrame` to split
  * `cols` : data frame columns to group by. Can be any column selector (`Symbol`, string or integer; `:`, `Cols`, `All`, `Between`, `Not`, a regular expression, or a vector of `Symbol`s, strings or integers). In particular if the selector picks no columns then a single-group `GroupedDataFrame` is created. As a special case, if `cols` is a single column or a vector of columns then it can contain columns wrapped in [`order`](@ref) that will be used to determine the order of groups if `sort` is `true` or a `NamedTuple` (if `sort` is `false`, then passing `order` is an error; if `sort` is `nothing` then it is set to `true` when `order` is passed).
  * `sort` : if `sort=true` sort groups according to the values of the grouping columns `cols`; if `sort=false` groups are created in their order of appearance in `df`; if `sort=nothing` (the default) then the fastest available grouping algorithm is picked and in consequence the order of groups in the result is undefined and may change in future releases; below a description of the current implementation is provided. Additionally `sort` can be a `NamedTuple` having some or all of `alg`, `lt`, `by`, `rev`, and `order` fields. In this case the groups are sorted and their order follows the [`sortperm`](@ref) order.
  * `skipmissing` : whether to skip groups with `missing` values in one of the grouping columns `cols`

# Details

An iterator over a `GroupedDataFrame` returns a `SubDataFrame` view for each grouping into `df`. Within each group, the order of rows in `df` is preserved.

A `GroupedDataFrame` also supports indexing by groups, `select`, `transform`, and `combine` (which applies a function to each group and combines the result into a data frame).

`GroupedDataFrame` also supports the dictionary interface. The keys are [`GroupKey`](@ref) objects returned by [`keys(::GroupedDataFrame)`](@ref), which can also be used to get the values of the grouping columns for each group. `Tuples` and `NamedTuple`s containing the values of the grouping columns (in the same order as the `cols` argument) are also accepted as indices. Finally, an `AbstractDict` can be used to index into a grouped data frame where the keys are column names of the data frame. The order of the keys does not matter in this case.

In the current implementation if `sort=nothing` groups are ordered following the order of appearance of values in the grouping columns, except when all grouping columns provide non-`nothing` `DataAPI.refpool`, in which case the order of groups follows the order of values returned by `DataAPI.refpool`. As a particular application of this rule if all `cols` are `CategoricalVector`s then groups are always sorted. Integer columns with a narrow range also use this this optimization, so to the order of groups when grouping on integer columns is undefined. A column is considered to be an integer column when deciding on the grouping algorithm choice if its `eltype` is a subtype of `Union{Missing, Real}`, all its elements are either `missing` or pass `isinteger` test, and none of them is equal to `-0.0`.

# See also

[`combine`](@ref), [`select`](@ref), [`select!`](@ref), [`transform`](@ref), [`transform!`](@ref)

# Examples

```jldoctest
julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),
                      b=repeat([2, 1], outer=[4]),
                      c=1:8);

julia> gd = groupby(df, :a)
GroupedDataFrame with 4 groups based on key: a
First Group (2 rows): a = 1
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5
⋮
Last Group (2 rows): a = 4
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     4      1      4
   2 │     4      1      8

julia> gd[1]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5

julia> last(gd)
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     4      1      4
   2 │     4      1      8

julia> gd[(a=3,)]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7

julia> gd[Dict("a" => 3)]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7

julia> gd[(3,)]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7

julia> k = first(keys(gd))
GroupKey: (a = 1,)

julia> gd[k]
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5

julia> for g in gd
           println(g)
       end
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      1
   2 │     1      2      5
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     2      1      2
   2 │     2      1      6
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     3      2      3
   2 │     3      2      7
2×3 SubDataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     4      1      4
   2 │     4      1      8
```
