```
O1_i(j)
```

Equivariant class of the pull-back of $\mathcal{O}_{\mathbb{P}^n}(1)$ with respect to the j-th evaluation map.

# Arguments

  * `j::Int64`: the evaluation map.

# Example

The following Gromov-Witten invariants

$$
\begin{aligned}
\int_{\overline{M}_{0,2}(\mathbb{P}^{1},1)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{1}}(1)\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{1}}(1) &= 1 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},1)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(2))) &= 4
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1_i(1)*O1_i(2);

julia> AtiyahBottFormula(1, 1, 2, P, show_bar=false);
Result: 1

julia> P = O1_i(1)^2*Hypersurface(2);

julia> AtiyahBottFormula(3, 1, 1, P, show_bar=false);
Result: 4
```

!!! warning "Attention!"
    The program will stop if `j` is not between 1 and the number of marks.

