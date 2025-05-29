Define one or more unknown variables.

```julia
@variables t α σ(..) β[1:2]
@variables w(..) x(t) y z(t, α, x)

expr = β[1]* x + y^α + σ(3) * (z - t) - β[2] * w(t - 1)
```

`(..)` signifies that the value should be left uncalled.

Symbolics supports creating variables that denote an array of some size.

```jldoctest
julia> @variables x[1:3]
1-element Vector{Symbolics.Arr{Num, 1}}:
 x[1:3]

julia> @variables y[1:3, 1:6] # support for  tensors
1-element Vector{Symbolics.Arr{Num, 2}}:
 y[1:3,1:6]

julia> @variables t z(t)[1:3] # also works for dependent variables
2-element Vector{Any}:
 t
  (z(t))[1:3]
```

A symbol or expression that represents an array can be turned into an array of symbols or expressions using the `scalarize` function.

```jldoctest
julia> Symbolics.scalarize(z)
3-element Vector{Num}:
 (z(t))[1]
 (z(t))[2]
 (z(t))[3]
```

Note that `@variables` returns a vector of all the defined variables.

`@variables` can also take runtime symbol values by the `$` interpolation operator, and in this case, `@variables` doesn't automatically assign the value, instead, it only returns a vector of symbolic variables. All the rest of the syntax also applies here.

```jldoctest
julia> a, b, c = :runtime_symbol_value, :value_b, :value_c
(:runtime_symbol_value, :value_b, :value_c)

julia> vars = @variables t $a $b(t) $c(t)[1:3]
4-element Vector{Any}:
      t
 runtime_symbol_value
   value_b(t)
       (value_c(t))[1:3]

julia> (t, a, b, c)
(t, :runtime_symbol_value, :value_b, :value_c)
```
