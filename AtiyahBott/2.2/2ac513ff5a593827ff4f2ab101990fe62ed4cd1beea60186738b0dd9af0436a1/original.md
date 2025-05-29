```
Incidency(r)
```

Equivariant class of the cycle parameterizing curves meeting a linear subspace of codimension `r`.

# Arguments

  * `r::Int64`: the codimension of the subvariety. Alternatively, it can be an array of integers, meaning the multiplication of the equivariant class defined by each element of the array.

# Example

The following Gromov-Witten invariants

$$
\begin{aligned}
\int_{\overline{M}_{0,0}(\mathbb{P}^{3},1)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{3})^{2} &= 1 \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{3},1)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2})^{2}\cdot \delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{3}) &= 1 \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{3},3)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2})^{2}\cdot \mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(3))) &= 756 \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = Incidency(3)^2;

julia> AtiyahBottFormula(3, 1, 0, P, show_bar=false);
Result: 1

julia> P = Incidency([2,2,3]);

julia> AtiyahBottFormula(3, 1, 0, P, show_bar=false);
Result: 1

julia> P = Incidency([2,2])*Hypersurface(3);

julia> AtiyahBottFormula(3, 3, 0, P, show_bar=false);
Result: 756
```

!!! warning "Attention!"
    The program will stop if `r` is not positive.

