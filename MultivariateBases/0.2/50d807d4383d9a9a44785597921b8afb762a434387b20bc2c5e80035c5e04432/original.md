```
abstract type AbstractMultipleOrthogonalBasis{P} <: AbstractPolynomialVectorBasis{P, Vector{P}} end
```

Polynomial basis such that $\langle p_i(x), p_j(x) \rangle = 0$ if $i \neq j$ where

$$
\langle p(x), q(x) \rangle = \int p(x)q(x) w(x) dx
$$

where the weight is a product of weight functions $w(x) = w_1(x_1)w_2(x_2) \cdots w_n(x_n)$ in each variable. The polynomial of the basis are product of univariate polynomials: $p(x) = p_1(x_1)p_2(x_2) \cdots p_n(x_n)$. where the univariate polynomials of variable `x_i` form an univariate orthogonal basis for the weight function `w_i(x_i)`. Therefore, they satisfy the recurrence relation

$$
d_k p_k(x_i) = (a_k x_i + b_k) p_{k-1}(x_i) + c_k p_{k-2}(x_i)
$$

where [`reccurence_first_coef`](@ref) gives `a_k`, [`reccurence_second_coef`](@ref) gives `b_k`, [`reccurence_third_coef`](@ref) gives `c_k` and [`reccurence_deno_coef`](@ref) gives `d_k`.
