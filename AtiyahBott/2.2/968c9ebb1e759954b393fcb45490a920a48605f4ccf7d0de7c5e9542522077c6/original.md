```
R1(k)
```

The equivariant class of the first derived functor of the pull-back of $\mathcal{O}_{\mathbb{P}^n}(-k)$.

# Arguments

  * `k::Int64`: a positive integer.

# Example

$$
\begin{aligned}
\int_{\overline{M}_{0,0}(\mathbb{P}^{1},d)}\mathrm{c_{top}}(R^{1}\delta_{*}(\mathrm{ev}^{*}\mathcal{O}_{\mathbb{P}^{3}}(-1)))^2 &= \frac{1}{d^3} \\
\end{aligned}
$$

can be computed as

```jldoctest; setup = :(using AtiyahBott)
julia> d = 1; #for other values of d, change this line

julia> P = R1(1)^2;

julia> AtiyahBottFormula(1, d, 0, P, show_bar=false);
Result: 1
```

!!! warning "Attention!"
    The program will stop if `k` is not positive.

