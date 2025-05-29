```
O1()
```

Equivariant class of the pull-back of $\mathcal{O}_{\mathbb{P}^n}(1)$ with respect to the product of all evaluation maps.

This function is equivalent to the product of the function `O1_i(j)` where `j` runs from 1 to the number of marks.

# Example

The following Gromov-Witten invariants

$$
\begin{aligned}
\int_{\overline{M}_{0,8}(\mathbb{P}^{2},3)}\prod_{i=1}^{8}\mathrm{ev}_{i}^{*}\mathcal{O}_{\mathbb{P}^{2}}(1)^2 &= 12 \\
\int_{\overline{M}_{0,1}(\mathbb{P}^{3},2)}\mathrm{ev}_{1}^{*}\mathcal{O}_{\mathbb{P}^{3}}(1)^2\cdot\mathrm{c_{top}}(\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(3))) &= 81 \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> P = O1()^2;

julia> AtiyahBottFormula(2, 3, 8, P, show_bar=false);
Result: 12

julia> P = O1()^2*Hypersurface(3);

julia> AtiyahBottFormula(3, 2, 1, P, show_bar=false);
Result: 81
```

In order to remove `O1_i(j)` for some `j`, it is enough to divide by that function.

# Example

```julia-repl
julia> P = O1()//O1_i(1);
```

Here `P` is the product of all `O1_i(j)` where `j` runs from 2 to `m`.
