```
 project(G::UnitaryMatrices, p)
 project(G::OrthogonalMatrices, p)
```

Project the point $p ∈ 𝔽^{n×n}$ to the nearest point in $\mathrm{U}(n,𝔽)=$[`Unitary(n,𝔽)`](@ref) under the Frobenius norm. If $p = U S V^\mathrm{H}$ is the singular value decomposition of $p$, then the projection is

$$
  \operatorname{proj}_{\mathrm{U}(n,𝔽)} \colon p ↦ U V^\mathrm{H}.
$$
