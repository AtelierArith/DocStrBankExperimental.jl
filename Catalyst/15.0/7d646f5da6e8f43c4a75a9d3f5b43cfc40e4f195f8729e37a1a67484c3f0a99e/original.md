```
@reaction
```

Macro for generating a single [`Reaction`](@ref) object using a similar syntax as the `@reaction_network` macro (but permitting only a single reaction). A more detailed introduction to the syntax can be found in the description of `@reaction_network`.

The `@reaction` macro is followed by a single line consisting of three parts:

  * A rate (at which the reaction occurs).
  * Any number of substrates (which are consumed by the reaction).
  * Any number of products (which are produced by the reaction).

The output is a reaction (just like created using the `Reaction` constructor).

Examples: Here we create a simple binding reaction and store it in the variable rx:

```julia
rx = @reaction k, X + Y --> XY
```

The macro will automatically deduce `X`, `Y`, and `XY` to be species (as these occur as reactants) and `k` as a parameter (as it does not occur as a reactant).

The `@reaction` macro provides a more concise notation to the `Reaction` constructor. I.e. here we create the same reaction using both approaches, and also confirm that they are identical.

```julia
# Creates a reaction using the `@reaction` macro.
rx = @reaction k*v, A + B --> C + D

# Creates a reaction using the `Reaction` constructor.
t = default_t()
@parameters k v
@species A(t) B(t) C(t) D(t)
rx2 = Reaction(k*v, [A, B], [C, D])

# Confirms that the two approaches yield identical results:
rx1 == rx2
```

Interpolation of already declared symbolic variables into `@reaction` is possible:

```julia
t = default_t()
@parameters k b
@species A(t)
ex = k*A^2 + t
rx = @reaction b*$ex*$A, $A --> C
```

Notes:

  * `@reaction` does not support bi-directional type reactions (using `<-->`) or reaction bundling

(e.g. `d, (X,Y) --> 0`).

  * Interpolation of Julia variables into the macro works similarly to the `@reaction_network`

macro. See [The Reaction DSL](@ref dsl_description) tutorial for more details.
