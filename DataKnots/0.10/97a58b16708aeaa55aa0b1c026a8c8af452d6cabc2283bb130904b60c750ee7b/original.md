```
DataKnot(Pair{Symbol}...)
```

This constructor binds names to datasets, so that they could be used to start a query. The knot created has a single top-level record, each with its own value.

```jldoctest
julia> test_knot = DataKnot(:dataset=>'a':'c')
│ dataset │
┼─────────┼
│ a; b; c │

julia> test_knot[It.dataset]
  │ dataset │
──┼─────────┼
1 │ a       │
2 │ b       │
3 │ c       │
```

Arguments to this constructor are run though `convert`.

---

```
convert(DataKnot, val)
```

This converter wraps a given value so that it could be used to start a query.

An empty knot can be constructed with `missing`.

```jldoctest
julia> convert(DataKnot, missing)
(empty)
```

A plural knot is constructed from a vector.

```jldoctest
julia> convert(DataKnot, 'a':'c')
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

An object that complies with the `Table` interface, such as a `CSV` file, can be converted to a DataKnot.

```jldoctest
julia> using CSV;

julia> csv_file = "k,v\na,1\nb,\n" |> IOBuffer |> CSV.File;

julia> convert(DataKnot, csv_file)
  │ k  v │
──┼──────┼
1 │ a  1 │
2 │ b    │
```

---

```
get(::DataKnot)
```

Use `get` to extract the underlying value held by a knot.

```jldoctest
julia> get(convert(DataKnot, "Hello World"))
"Hello World"
```

---

```
getindex(::DataKnot, X; kwargs...)
```

We can query a knot using array indexing notation.

```jldoctest
julia> convert(DataKnot, (dataset='a':'c',))[Count(It.dataset)]
┼───┼
│ 3 │
```

Query parameters are provided as keyword arguments.

```jldoctest
julia> convert(DataKnot, 1:3)[PWR=2, It .^ It.PWR]
──┼───┼
1 │ 1 │
2 │ 4 │
3 │ 9 │
```
