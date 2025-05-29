Construct the canonical gate for the given Weyl chamber coordinates.

```julia
Û = canonical_gate(c₁, c₂, c₃)
```

constructs the two qubit gate $Û$ as

$$
Û = \exp\left[i\frac{π}{2} (c_1 σ̂_x σ̂_x + c_2 σ̂_y σ̂_y + c_3 σ̂_z σ̂_z)\right]
$$

where $σ̂_{x,y,z}$ are the Pauli matrices.
