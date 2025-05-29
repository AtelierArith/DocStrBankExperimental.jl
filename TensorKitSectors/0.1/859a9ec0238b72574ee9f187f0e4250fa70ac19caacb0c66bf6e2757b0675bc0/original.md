```
struct IsingAnyon <: Sector
IsingAnyon(s::Symbol)
```

Represents the anyons of the Ising modular fusion category. It can take three values, corresponding to the trivial sector `IsingAnyon(:I)` and the non-trivial sectors `IsingAnyon(:σ)` and `IsingAnyon(:ψ)`, with fusion rules $ψ ⊗ ψ = 1$, $σ ⊗ ψ = σ$, and $σ ⊗ σ = 1 ⊕ ψ$.

## Fields

  * `s::Symbol`: the label of the represented anyon, which can be `:I`, `:σ`, or `:ψ`.
