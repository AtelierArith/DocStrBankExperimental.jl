```
table(cols; kw...)
```

Create a table from a (named) tuple of AbstractVectors.

```
table(cols::AbstractVector...; names::Vector{Symbol}, kw...)
```

Create a table from the provided `cols`, optionally with `names`.

```
table(cols::Columns; kw...)
```

Construct a table from a vector of tuples. See [`rows`](@ref) and [`Columns`](@ref).

```
table(t::Union{IndexedTable, NDSparse}; kw...)
```

Copy a Table or NDSparse to create a new table. The same primary keys as the input are used.

```
table(x; kw...)
```

Create an `IndexedTable` from any object `x` that follows the `Tables.jl` interface.

# Keyword Argument Options:

  * `pkey`: select columns to sort by and be the primary key.
  * `presorted = false`: is the data pre-sorted by primary key columns?
  * `copy = true`: creates a copy of the input vectors if `true`. Irrelevant if `chunks` is specified.
  * `chunks::Integer`: distribute the table.  Options are:

      * `Int` – (number of chunks) a safe bet is `nworkers()` after `using Distributed`.
      * `Vector{Int}` – Number of elements in each of the `length(chunks)` chunks.

# Examples:

```
table(rand(10), rand(10), names = [:x, :y], pkey = :x)

table(rand(Bool, 20), rand(20), rand(20), pkey = [1,2])

table((x = 1:10, y = randn(10)))

table([(1,2), (3,4)])
```
