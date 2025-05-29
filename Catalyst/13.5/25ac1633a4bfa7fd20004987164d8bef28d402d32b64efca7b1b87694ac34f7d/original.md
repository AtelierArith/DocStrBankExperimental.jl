```
@reaction
```

Generates a single [`Reaction`](@ref) object.

Examples:

```julia
rx = @reaction k*v, A + B --> C + D

# is equivalent to
@parameters k v
@variables t
@species A(t) B(t) C(t) D(t)
rx == Reaction(k*v, [A,B], [C,D])
```

Here `k` and `v` will be parameters and `A`, `B`, `C` and `D` will be variables. Interpolation of existing parameters/variables also works

```julia
@parameters k b
@variables t
@species A(t)
ex = k*A^2 + t
rx = @reaction b*$ex*$A, $A --> C
```

Notes:

  * Any symbols arising in the rate expression that aren't interpolated are treated as parameters. In the reaction part (`α*A + B --> C + D`), coefficients are treated as parameters, e.g. `α`, and rightmost symbols as species, e.g. `A,B,C,D`.
  * Works with any *single* arrow types supported by [`@reaction_network`](@ref).
  * Interpolation of Julia variables into the macro works similar to the `@reaction_network` macro. See [The Reaction DSL](@ref dsl_description) tutorial for more details.
