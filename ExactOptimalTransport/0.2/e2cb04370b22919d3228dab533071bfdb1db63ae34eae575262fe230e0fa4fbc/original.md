```
emd(μ, ν, C, optimizer)
```

Compute the optimal transport plan `γ` for the Monge-Kantorovich problem with source histogram `μ`, target histogram `ν`, and cost matrix `C` of size `(length(μ), length(ν))` which solves

$$
\inf_{γ ∈ Π(μ, ν)} \langle γ, C \rangle.
$$

The corresponding linear programming problem is solved with the user-provided `optimizer`. Possible choices are `Tulip.Optimizer()` and `Clp.Optimizer()` in the `Tulip` and `Clp` packages, respectively.
