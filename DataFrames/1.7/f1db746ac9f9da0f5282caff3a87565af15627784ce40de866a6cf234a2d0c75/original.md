```
DataFrame <: AbstractDataFrame
```

An `AbstractDataFrame` that stores a set of named columns.

The columns are normally `AbstractVector`s stored in memory, particularly a `Vector`, `PooledVector` or `CategoricalVector`.

# Constructors

```julia
DataFrame(pairs::Pair...; makeunique::Bool=false, copycols::Bool=true)
DataFrame(pairs::AbstractVector{<:Pair}; makeunique::Bool=false, copycols::Bool=true)
DataFrame(ds::AbstractDict; copycols::Bool=true)
DataFrame(; kwargs..., copycols::Bool=true)

DataFrame(table; copycols::Union{Bool, Nothing}=nothing)
DataFrame(table, names::AbstractVector;
          makeunique::Bool=false, copycols::Union{Bool, Nothing}=nothing)
DataFrame(columns::AbstractVecOrMat, names::AbstractVector;
          makeunique::Bool=false, copycols::Bool=true)

DataFrame(::DataFrameRow; copycols::Bool=true)
DataFrame(::GroupedDataFrame; copycols::Bool=true, keepkeys::Bool=true)
```

# Keyword arguments

  * `copycols` : whether vectors passed as columns should be copied; by default set to `true` and the vectors are copied; if set to `false` then the constructor will still copy the passed columns if it is not possible to construct a `DataFrame` without materializing new columns. Note the `copycols=nothing` default in the Tables.jl compatible constructor; it is provided as certain input table types may have already made a copy of columns or the columns may otherwise be immutable, in which case columns are not copied by default. To force a copy in such cases, or to get mutable columns from an immutable input table (like `Arrow.Table`), pass `copycols=true` explicitly.
  * `makeunique` : if `false` (the default), an error will be raised

(note that not all constructors support these keyword arguments)

# Details on behavior of different constructors

It is allowed to pass a vector of `Pair`s, a list of `Pair`s as positional arguments, or a list of keyword arguments. In this case each pair is considered to represent a column name to column value mapping and column name must be a `Symbol` or string. Alternatively a dictionary can be passed to the constructor in which case its entries are considered to define the column name and column value pairs. If the dictionary is a `Dict` then column names will be sorted in the returned `DataFrame`.

In all the constructors described above column value can be a vector which is consumed as is or an object of any other type (except `AbstractArray`). In the latter case the passed value is automatically repeated to fill a new vector of the appropriate length. As a particular rule values stored in a `Ref` or a `0`-dimensional `AbstractArray` are unwrapped and treated in the same way.

It is also allowed to pass a vector of vectors or a matrix as as the first argument. In this case the second argument must be a vector of `Symbol`s or strings specifying column names, or the symbol `:auto` to generate column names `x1`, `x2`, ... automatically. Note that in this case if the first argument is a matrix and `copycols=false` the columns of the created `DataFrame` will be views of columns the source matrix.

If a single positional argument is passed to a `DataFrame` constructor then it is assumed to be of type that implements the [Tables.jl](https://github.com/JuliaData/Tables.jl) interface using which the returned `DataFrame` is materialized.

If two positional arguments are passed, where the second argument is an `AbstractVector`, then the first argument is taken to be a table as described in the previous paragraph, and columns names of the resulting data frame are taken from the vector passed as the second positional argument.

Finally it is allowed to construct a `DataFrame` from a `DataFrameRow` or a `GroupedDataFrame`. In the latter case the `keepkeys` keyword argument specifies whether the resulting `DataFrame` should contain the grouping columns of the passed `GroupedDataFrame` and the order of rows in the result follows the order of groups in the `GroupedDataFrame` passed.

# Notes

The `DataFrame` constructor by default copies all columns vectors passed to it. Pass the `copycols=false` keyword argument (where supported) to reuse vectors without copying them.

By default an error will be raised if duplicates in column names are found. Pass `makeunique=true` keyword argument (where supported) to accept duplicate names, in which case they will be suffixed with `_i` (`i` starting at 1 for the first duplicate).

If an `AbstractRange` is passed to a `DataFrame` constructor as a column it is always collected to a `Vector` (even if `copycols=false`). As a general rule `AbstractRange` values are always materialized to a `Vector` by all functions in DataFrames.jl before being stored in a `DataFrame`.

`DataFrame` can store only columns that use 1-based indexing. Attempting to store a vector using non-standard indexing raises an error.

The `DataFrame` type is designed to allow column types to vary and to be dynamically changed also after it is constructed. Therefore `DataFrame`s are not type stable. For performance-critical code that requires type-stability either use the functionality provided by `select`/`transform`/`combine` functions, use `Tables.columntable` and `Tables.namedtupleiterator` functions, use barrier functions, or provide type assertions to the variables that hold columns extracted from a `DataFrame`.

Metadata: this function preserves all table and column-level metadata. As a special case if a `GroupedDataFrame` is passed then only `:note`-style metadata from parent of the `GroupedDataFrame` is preserved.

# Examples

```jldoctest
julia> DataFrame((a=[1, 2], b=[3, 4])) # Tables.jl table constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      3
   2 │     2      4

julia> DataFrame([(a=1, b=0), (a=2, b=0)]) # Tables.jl table constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame("a" => 1:2, "b" => 0) # Pair constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame([:a => 1:2, :b => 0]) # vector of Pairs constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame(Dict(:a => 1:2, :b => 0)) # dictionary constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame(a=1:2, b=0) # keyword argument constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame([[1, 2], [0, 0]], [:a, :b]) # vector of vectors constructor
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0

julia> DataFrame([1 0; 2 0], :auto) # matrix constructor
2×2 DataFrame
 Row │ x1     x2
     │ Int64  Int64
─────┼──────────────
   1 │     1      0
   2 │     2      0
```
