```
intervene(ct::CausalTable, intervention::Function)
```

Applies `intervention` to the treatment vector(s) within a CausalTable, and outputs a new CausalTable with the intervened treatment.

# Arguments

  * `ct::CausalTable`: The data on which treatment should be intervened
  * `intervention::Function`: A function that defines the intervention to be applied to the parent variables. Use `cast_matrix_to_table_function` to convert a function acting on a treatment vector or matrix to a function that acts on a `CausalTable`.

# Returns

A `CausalTable` containing the same data as `ct`, but with the treatment variable(s) modified accoding to `intervention`

# Example

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
ct = rand(scm, 100)
intervene(ct, treat_all)
```
