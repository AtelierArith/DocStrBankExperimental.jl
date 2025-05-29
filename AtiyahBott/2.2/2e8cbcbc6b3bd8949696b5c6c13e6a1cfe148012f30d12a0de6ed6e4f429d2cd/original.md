```
Jet(p, q)
```

Equivariant class of the jet bundle $J^p$ of the pull back of $\mathcal{O}_{\mathbb{P}^n}(q)$ with respect to the first $\psi$-class.

# Arguments

  * `p::Int64`: the exponent of the Jet bundle. In particular, it is a bundle of rank $p+1$.
  * `q::Int64`: the degree of the line bundle that is pulled back.

!!! note
    In order to define this bundle, the number of marks must be at least 1. You cannot multiply this bundle by the class `Psi(a)`.


# Example

$$
\begin{aligned}
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2})^{4}\cdot\mathrm{c_{top}}(J^{1}(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1))) &= 2 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{2},2)}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2})^{4}\cdot(\mathrm{c_{top}}(J^{1}(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)))+\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^{2}) &= 3 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},d)}\frac{\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^{2}}{k}\cdot\mathrm{c_{top}}(J^{4d-2}(\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(k))) &= \frac{(4d-2)!}{(d!)^{4}} \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = Incidency(2)^4*Jet(1,1);

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false);
Result: 2

julia> P = Incidency(2)^4*(Jet(1,1)+O1()^2);

julia> AtiyahBottFormula(2, 2, 1, P, show_bar=false);
Result: 3

julia> d=1;k=1; #for other values of d, change this line

julia> P = (O1()^2)//k*Jet(4*d-2,k);

julia> AtiyahBottFormula(3, d, 1, P, show_bar=false);   #The value of this integral does not depend on k, only on d
Result: 2
```
