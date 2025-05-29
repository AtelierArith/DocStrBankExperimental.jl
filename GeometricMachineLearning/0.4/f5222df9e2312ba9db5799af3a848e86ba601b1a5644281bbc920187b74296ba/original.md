```
AdamOptimizer(η, ρ₁, ρ₂, δ)
```

Make an instance of the Adam Optimizer.

Here the cache consists of first and second moments that are updated as 

$$
B_1 \gets ((\rho_1 - \rho_1^t)/(1 - \rho_1^t))\cdot{}B_1 + (1 - \rho_1)/(1 - \rho_1^t)\cdot{}\nabla{}L,
$$

and

$$
B_2 \gets ((\rho_2 - \rho_1^t)/(1 - \rho_2^t))\cdot{}B_2 + (1 - \rho_2)/(1 - \rho_2^t)\cdot\nabla{}L\odot\nabla{}L.
$$

The final velocity is computed as:

$$
\mathrm{velocity} \gets -\eta{}B_1/\sqrt{B_2 + \delta}.
$$

# Implementation

The *velocity* is stored in the input to save memory:

```julia
mul!(B, -o.method.η, /ᵉˡᵉ(C.B₁, scalar_add(racᵉˡᵉ(C.B₂), o.method.δ)))
```

where `B` is the input to the [`update!`] function.

The algorithm and suggested defaults are taken from [goodfellow2016deep; page 301](@cite).
