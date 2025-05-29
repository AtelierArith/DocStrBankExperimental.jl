```
multiplicative_mtp(δ)
```

Constructs a function that scales the treatment variable(s) in a `CausalTable` object by a constant δ. This function is intended to be used as an argument to `ape`.

# Arguments

  * δ: The "multiplicative shift" to be applied to the treatment variable of a `CausalTable`.

# Returns

  * A function that takes a `CausalTable` object as input and returns a column table of treatments that have been scaled by δ units.

# Example

```@example
using Distributions
dgp = CausalTables.@dgp(
    L ~ Beta(2, 4),
    A ~ @.(Normal(L)),
    Y ~ @.(Normal(A + 2 * L + 1))
)
scm = CausalTables.StructuralCausalModel(dgp, [:A], [:Y], [:L])
ape(scm, multiplicative_mtp(2.0))
```
