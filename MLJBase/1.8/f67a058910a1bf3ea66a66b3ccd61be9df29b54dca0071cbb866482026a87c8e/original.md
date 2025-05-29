```
unpack(table, f1, f2, ... fk;
       wrap_singles=false,
       shuffle=false,
       rng::Union{AbstractRNG,Int,Nothing}=nothing,
       coerce_options...)
```

Horizontally split any Tables.jl compatible `table` into smaller tables or vectors by making column selections determined by the predicates `f1`, `f2`, ..., `fk`. Selection from the column names is without replacement. A *predicate* is any object `f` such that `f(name)` is `true` or `false` for each column `name::Symbol` of `table`.

Returns a tuple of tables/vectors with length one greater than the number of supplied predicates, with the last component including all previously unselected columns.

```julia-repl
julia> table = DataFrame(x=[1,2], y=['a', 'b'], z=[10.0, 20.0], w=["A", "B"])
2×4 DataFrame
 Row │ x      y     z        w
     │ Int64  Char  Float64  String
─────┼──────────────────────────────
   1 │     1  a        10.0  A
   2 │     2  b        20.0  B

julia> Z, XY, W = unpack(table, ==(:z), !=(:w));
julia> Z
2-element Vector{Float64}:
 10.0
 20.0

julia> XY
2×2 DataFrame
 Row │ x      y
     │ Int64  Char
─────┼─────────────
   1 │     1  a
   2 │     2  b

julia> W  # the column(s) left over
2-element Vector{String}:
 "A"
 "B"
```

Whenever a returned table contains a single column, it is converted to a vector unless `wrap_singles=true`.

If `coerce_options` are specified then `table` is first replaced with `coerce(table, coerce_options)`. See [`ScientificTypes.coerce`](@ref) for details.

If `shuffle=true` then the rows of `table` are first shuffled, using the global RNG, unless `rng` is specified; if `rng` is an integer, it specifies the seed of an automatically generated Mersenne twister. If `rng` is specified then `shuffle=true` is implicit.
