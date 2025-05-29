```
Hypersurface(b)
```

Equivariant class of the Euler class of the bundle equal to the direct image under the forgetful map of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(b)$. It parameterizes curves contained in a hypersurface of degree `b`.

# Arguments

  * `b::Int64`: the degrees of the hypersurface. Alternatively, it can be an array of integers, meaning the multiplication of the equivariant class defined by each element of the array.

# Example

The following Gromov-Witten invariants of Calabi-Yau threefolds

$$
\begin{aligned}
\int_{\overline{M}_{0,0}(\mathbb{P}^{4},1)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{4}}(5))) &= 2875 \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{5},2)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{5}}(3))^{\oplus 2}) &= \frac{423549}{8} \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{5},3)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{5}}(4)))\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{5}}(2))) &= \frac{422690816}{27} \\
\int_{\overline{M}_{0,0}(\mathbb{P}^{7},4)}\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{7}}(2)))^4 &= 25705160 \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = Hypersurface(5);

julia> AtiyahBottFormula(4, 1, 0, P, show_bar=false);
Result: 2875

julia> P = Hypersurface([3,3]);

julia> AtiyahBottFormula(5, 2, 0, P, show_bar=false);
Result: 423549//8

julia> P = Hypersurface(4)*Hypersurface(2);

julia> AtiyahBottFormula(5, 3, 0, P, show_bar=false);
Result: 422690816//27

julia> P = Hypersurface(2)^4;

julia> AtiyahBottFormula(7, 4, 0, P, show_bar=false);
Result: 25705160
```

!!! warning "Attention!"
    The program will stop if `b` is not positive.

