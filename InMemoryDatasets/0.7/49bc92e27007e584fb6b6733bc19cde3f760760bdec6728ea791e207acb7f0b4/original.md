```
Dataset <: AbstractDataset
```

An AbstractDataset that stores a set of named columns

The columns are normally AbstractVectors stored in memory.

# Constructors

```julia
Dataset(pairs::Pair...; makeunique::Bool=false)
Dataset(pairs::AbstractVector{<:Pair}; makeunique::Bool=false)
Dataset(ds::AbstractDict)
Dataset(kwargs...)

Dataset(columns::AbstractVecOrMat, names::Union{AbstractVector, Symbol};
          makeunique::Bool=false)

Dataset(table)
Dataset(::DatasetRow)
```

# Keyword arguments

  * `makeunique` : if `false` (the default), an error will be raised

(note that not all constructors support these keyword arguments)

# Details on behavior of different constructors

It is allowed to pass a vector of `Pair`s, a list of `Pair`s as positional arguments, or a list of keyword arguments. In this case each pair is considered to represent a column name to column value mapping and column name must be a `Symbol` or string. Alternatively a dictionary can be passed to the constructor in which case its entries are considered to define the column name and column value pairs. If the dictionary is a `Dict` then column names will be sorted in the returned `Dataset`.

In all the constructors described above column value can be a vector which is consumed as is or an object of any other type (except `AbstractArray`). In the latter case the passed value is automatically repeated to fill a new vector of the appropriate length. As a particular rule values stored in a `Ref` or a `0`-dimensional `AbstractArray` are unwrapped and treated in the same way.

It is also allowed to pass a vector of vectors or a matrix as as the first argument. In this case the second argument must be a vector of `Symbol`s or strings specifying column names, or the symbol `:auto` to generate column names `x1`, `x2`, ... automatically.

If a single positional argument is passed to a `Dataset` constructor then it is assumed to be of type that implements the [Tables.jl](https://github.com/JuliaData/Tables.jl) interface using which the returned `Dataset` is materialized.

Finally it is allowed to construct a `Dataset` from a `DatasetRow`.

# Notes

The `allowmissing` function is called on all columns passed to constructor before being added to the output data set.

By default an error will be raised if duplicates in column names are found. Pass `makeunique=true` keyword argument (where supported) to accept duplicate names, in which case they will be suffixed with `_i` (`i` starting at 1 for the first duplicate).

If an `AbstractRange` is passed to a `Dataset` constructor as a column it is always collected to a `Vector`. As a general rule `AbstractRange` values are always materialized to a `Vector` by all functions in InMemoryDatasets.jl before being stored in a `Dataset`.

`Dataset` can store only columns that use 1-based indexing. Attempting to store a vector using non-standard indexing raises an error.

The `Dataset` type is designed to allow column types to vary and to be dynamically changed also after it is constructed.

# Examples

```jldoctest
julia> Dataset((a=[1, 2], b=[3, 4])) # Tables.jl table constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         3
   2 │        2         4

julia> Dataset([(a=1, b=0), (a=2, b=0)]) # Tables.jl table constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset("a" => 1:2, "b" => 0) # Pair constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset([:a => 1:2, :b => 0]) # vector of Pairs constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset(Dict(:a => 1:2, :b => 0)) # dictionary constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset(a=1:2, b=0) # keyword argument constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset([[1, 2], [0, 0]], [:a, :b]) # vector of vectors constructor
2×2 Dataset
 Row │ a         b
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0

julia> Dataset([1 0; 2 0], :auto) # matrix constructor
2×2 Dataset
 Row │ x1        x2
     │ identity  identity
     │ Int64?    Int64?
─────┼────────────────────
   1 │        1         0
   2 │        2         0
```
