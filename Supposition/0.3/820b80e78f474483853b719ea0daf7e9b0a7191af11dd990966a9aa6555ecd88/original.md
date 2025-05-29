```
example(gen::Possibility, n::Integer; tries=100_000)
```

Generate `n` examples for the given `Possibility`. Each example is given `tries` attempts to generate. If any fail, the entire process is aborted.

```julia-repl
julia> using Supposition, Supposition.Data

julia> is = Data.Integers(0, 10);

julia> example(is, 10)
10-element Vector{Int64}:
  9
  1
  4
  4
  7
  4
  6
 10
  1
  8
```
