```julia
struct Reaction{S, T}
```

One chemical reaction.

# Fields

  * `rate`: The rate function (excluding mass action terms).
  * `substrates`: Reaction substrates.
  * `products`: Reaction products.
  * `substoich`: The stoichiometric coefficients of the reactants.
  * `prodstoich`: The stoichiometric coefficients of the products.
  * `netstoich`: The net stoichiometric coefficients of all species changed by the reaction.
  * `only_use_rate`: `false` (default) if `rate` should be multiplied by mass action terms to give the rate law. `true` if `rate` represents the full reaction rate law.

  * `metadata`: Contain additional data, such whenever the reaction have a specific noise-scaling expression for the chemical Langevin equation.

# Examples

```julia
using Catalyst
t = default_t()
@parameters k[1:20]
@species A(t) B(t) C(t) D(t)
rxs = [Reaction(k[1], nothing, [A]),            # 0 -> A
       Reaction(k[2], [B], nothing),            # B -> 0
       Reaction(k[3],[A],[C]),                  # A -> C
       Reaction(k[4], [C], [A,B]),              # C -> A + B
       Reaction(k[5], [C], [A], [1], [2]),      # C -> A + A
       Reaction(k[6], [A,B], [C]),              # A + B -> C
       Reaction(k[7], [B], [A], [2], [1]),      # 2B -> A
       Reaction(k[8], [A,B], [A,C]),            # A + B -> A + C
       Reaction(k[9], [A,B], [C,D]),            # A + B -> C + D
       Reaction(k[10], [A], [C,D], [2], [1,1]), # 2A -> C + D
       Reaction(k[11], [A], [A,B], [2], [1,1]), # 2A -> A + B
       Reaction(k[12], [A,B,C], [C,D], [1,3,4], [2, 3]),          # A+3B+4C -> 2C + 3D
       Reaction(k[13], [A,B], nothing, [3,1], nothing),           # 3A+B -> 0
       Reaction(k[14], nothing, [A], nothing, [2]),               # 0 -> 2A
       Reaction(k[15]*A/(2+A), [A], nothing; only_use_rate=true), # A -> 0 with custom rate
       Reaction(k[16], [A], [B]; only_use_rate=true),             # A -> B with custom rate.
       Reaction(k[17]*A*exp(B), [C], [D], [2], [1]),              # 2C -> D with non constant rate.
       Reaction(k[18]*B, nothing, [B], nothing, [2]),             # 0 -> 2B with non constant rate.
       Reaction(k[19]*t, [A], [B]),                                # A -> B with non constant rate.
       Reaction(k[20]*t*A, [B,C], [D],[2,1],[2])                  # 2A +B -> 2C with non constant rate.
  ]
```

Notes:

  * `nothing` can be used to indicate a reaction that has no reactants or no products. In this case the corresponding stoichiometry vector should also be set to `nothing`.
  * The three-argument form assumes all reactant and product stoichiometric coefficients are one.
