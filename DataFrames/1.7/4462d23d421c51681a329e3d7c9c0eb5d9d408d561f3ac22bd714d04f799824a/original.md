```
AbstractDataFrame
```

An abstract type for which all concrete types expose an interface for working with tabular data.

An `AbstractDataFrame` is a two-dimensional table with `Symbol`s or strings for column names.

DataFrames.jl defines two types that are subtypes of `AbstractDataFrame`: [`DataFrame`](@ref) and [`SubDataFrame`](@ref).

# Indexing and broadcasting

`AbstractDataFrame` can be indexed by passing two indices specifying row and column selectors. The allowed indices are a superset of indices that can be used for standard arrays. You can also access a single column of an `AbstractDataFrame` using `getproperty` and `setproperty!` functions. Columns can be selected using integers, `Symbol`s, or strings. In broadcasting `AbstractDataFrame` behavior is similar to a `Matrix`.

A detailed description of `getindex`, `setindex!`, `getproperty`, `setproperty!`, broadcasting and broadcasting assignment for data frames is given in the ["Indexing" section](https://juliadata.github.io/DataFrames.jl/stable/lib/indexing/) of the manual.
