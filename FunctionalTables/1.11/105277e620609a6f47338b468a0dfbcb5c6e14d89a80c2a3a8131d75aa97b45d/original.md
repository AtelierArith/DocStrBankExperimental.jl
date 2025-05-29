```julia
by(ft, splitkeys)

```

An iterator that groups rows of tables by the columns `splitkeys`, returning `(index::NamedTupe, table::FunctionalTable)` for each contiguous block of the index keys.

The function has a convenience form `by(ft, splitkeys...; ...)`.
