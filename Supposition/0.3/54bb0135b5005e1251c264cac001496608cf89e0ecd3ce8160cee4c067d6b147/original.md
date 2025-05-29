```
example(pos::Possibility; tries=100_000, generation::Int)
```

Generate an example for the given `Possibility`.

`example` tries to have `pos` produce an example `tries` times and throws an error if `pos` doesn't produce one in that timeframe. `generation` indicates how "late" in a usual run of `@check` the example might have been generated.

Usage:

```julia-repl
julia> using Supposition, Supposition.Data

julia> example(Data.Integers(0, 10))
7
```
