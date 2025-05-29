```
additive_mtp(δ)
```

Constructs a function that adds a constant (or constant vector) δ to the treatment variable(s) in a `CausalTable` object. This function is intended to be used as an argument to `ape`.

# Arguments

  * δ: The "additive shift" to be applied to the treatment variable of a `CausalTable`.

# Returns

  * A function that takes a `CausalTable` object as input and returns a column table of treatments that have been shifted by δ units.

# Example

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Normal(L)),
    Y ~ @.(Normal(A + 2 * L + 1))
)
scm = StructuralCausalModel(dgp, [:A], [:Y], [:L])
ape(scm, additive_mtp(0.5))
```
