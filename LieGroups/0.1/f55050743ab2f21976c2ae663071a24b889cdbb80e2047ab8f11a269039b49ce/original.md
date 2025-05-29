```
RightSemidirectProductGroupOperation{O1,O2,A} <: SemiDirectProductGroupOperation{O1,O2,A}
```

A struct to model a right semidirect Lie group product.

Let $(\mathcal N, ⋄)$ and $(\mathcal H, ⋆)$ be two Lie groups with group operations $⋄$ and $⋆$, respectively, as well as a group action $σ: \mathcal H×\mathcal N → \mathcal N$, cf [`AbstractGroupActionType`](#ref).

We use here as well use the notation $σ_h: \mathcal N → \mathcal N$ as a family of maps on $\mathcal N$

Then we define a group operation $∘$ on the product manifold $\mathcal N×\mathcal H$ by

$$
    (n_1,h_1) ∘ (n_2,h_2) := (n_1 ⋄ σ_{h_1}(n_2), h_1 ⋆ h_2)
$$

See [HilgertNeeb:2012; Definition 9.2.22](@cite), first definition for more details.

# Constructor

```
RightSemidirectProductGroupOperation(
    op1::AbstractGroupOperation,
    op2::AbstractGroupOperation,
    action::AbstractGroupActionType
)
```

# Parameters

  * `op1::AbstractGroupOperation`: The group operation $⋆$ on $\mathcal N$
  * `op2::AbstractGroupOperation`: The group operation $⋄$ on $\mathcal H$
  * `action::AbstractGroupActionType`: The group action $σ$ of $\mathcal H$ on $\mathcal N$
