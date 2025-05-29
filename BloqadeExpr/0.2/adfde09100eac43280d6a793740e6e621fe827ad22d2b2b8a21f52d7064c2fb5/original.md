```
struct RydInteract{D} <: AbstractTerm{D}
RydInteract(;atoms, C=2π * 862690MHz⋅μm^6)
```

Type for Rydberg interactive term.

# Expression

$$
\sum_{i, j} \frac{C}{|x_i - x_j|^6} n_i n_j
$$

# Keyword Arguments

  * `atoms`: a list of atom positions, must be type `RydAtom`, default unit is `μm`.
  * `C`: the interaction strength, default unit is `MHz⋅μm^6`. default value is `2π * 862690 * MHz*µm^6`.
