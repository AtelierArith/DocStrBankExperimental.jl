```
LeftSemidirectProductGroupOperation{O1,O2,A} <: SemiDirectProductGroupOperation{O1,O2,A}
```

A struct to model a semidirect Lie group product.

Let $(\mathcal N, ⋄)$ and $(\mathcal H, ⋆)$ be two Lie groups with group operations $⋄$ and $⋆$, respectively, as well as a group action $σ: \mathcal H×\mathcal N → \mathcal N$, cf [`AbstractLeftGroupActionType`](@ref).

We use here as well use the notation $σ_h: \mathcal N → \mathcal N$ as a family of maps on $\mathcal N$

Then we define a group operation $∘$ on the product manifold $\mathcal N×\mathcal H$ by

$$
    (h_1,n_1) ∘ (h_2,n_2) := (h_1 ⋆ h_2, σ_{h_2}(n_1) ⋄ n_2).
$$

See [HilgertNeeb:2012; Definition 9.2.22](@cite), second definition for more details.

# Constructor

```
LeftSemidirectProductGroupOperation(
    op1::AbstractGroupOperation,
    op2::AbstractGroupOperation,
    action::AbstractGroupActionType
)
```

# Parameters

  * `op1::AbstractGroupOperation`: The group operation $⋄$ on $\mathcal H$
  * `op2::AbstractGroupOperation`: The group operation $⋆$ on $\mathcal N$
  * `action::AbstractGroupActionType` The group action $σ$ of $\mathcal H$ on $\mathcal N$
