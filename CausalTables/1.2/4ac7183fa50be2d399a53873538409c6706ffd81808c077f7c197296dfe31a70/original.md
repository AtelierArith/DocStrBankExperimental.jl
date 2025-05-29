```
treat_all(ct::CausalTable)
```

Intervenes on a `CausalTable` object by setting all treatment variables to 1.

# Arguments

  * `ct::CausalTable`: A `CausalTable` object with a univariate binary treatment.

# Returns

A `NamedTuple` object with the same header as the treatment matrix in `ct`, where each treatment variable is set to 1.

# Example

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
data = rand(scm, 100)
treat_all(data)
```
