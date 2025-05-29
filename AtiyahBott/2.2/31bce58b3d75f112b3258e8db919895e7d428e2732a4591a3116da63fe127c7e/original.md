```
Contact()
```

Equivariant class of the Euler class of the bundle equal to the direct image under the forgetful map of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(2)$ tensor the dualizing sheaf of the forgetful map. It parameterizes contact curves in an odd dimensional projective space.

# Example

$$
\begin{aligned}
\int_{\overline{M}_{0,2}(\mathbb{P}^{3},1)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2}\cdot\mathrm{ev}_{2}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{3}\cdot\mathrm{c_{top}}(\delta_{*}(\omega_{\delta}\otimes\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(2))) &= 1 \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1_i(1)^2*O1_i(2)^3*Contact();

julia> AtiyahBottFormula(3, 1, 2, P, show_bar=false);
Result: 1
```
