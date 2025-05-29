```
cosets(G, H)
```

For a subgroup `H` $=H$ of `G` = $G$, find a set of (left) coset representatives  $\{g_i\}$ of $H$ in $G$, such that (see e.g., Inui et al., Section 2.7)

$$
    G = \bigcup_i g_i H.
$$

The identity operation $1$ is always included in $\{g_i\}$.

## Example

```jldoctest cosets
julia> G = pointgroup("6mm");

julia> H = pointgroup("3");

julia> Q = cosets(G, H)
4-element Vector{SymOperation{3}}:
 1
 2₀₀₁
 m₁₁₀
 m₋₁₁₀
```

To generate the associated cosets, simply compose the representatives with `H`:

```jldoctest cosets
julia> [compose.(Ref(q), H) for q in Q]
4-element Vector{Vector{SymOperation{3}}}:
 [1, 3₀₀₁⁺, 3₀₀₁⁻]
 [2₀₀₁, 6₀₀₁⁻, 6₀₀₁⁺]
 [m₁₁₀, m₁₀₀, m₀₁₀]
 [m₋₁₁₀, m₁₂₀, m₂₁₀]
```
