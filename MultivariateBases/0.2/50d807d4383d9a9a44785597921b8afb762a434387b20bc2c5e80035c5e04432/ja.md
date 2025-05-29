```
抽象型 AbstractMultipleOrthogonalBasis{P} <: AbstractPolynomialVectorBasis{P, Vector{P}} end
```

多項式基底は、$\langle p_i(x), p_j(x) \rangle = 0$ である場合、$i \neq j$ です。

$$
\langle p(x), q(x) \rangle = \int p(x)q(x) w(x) dx
$$

ここで、重みは各変数における重み関数の積であり、$w(x) = w_1(x_1)w_2(x_2) \cdots w_n(x_n)$ です。基底の多項式は一変数多項式の積であり、$p(x) = p_1(x_1)p_2(x_2) \cdots p_n(x_n)$ です。変数 `x_i` の一変数多項式は、重み関数 `w_i(x_i)` に対する一変数直交基底を形成します。したがって、彼らは再帰関係を満たします。

$$
d_k p_k(x_i) = (a_k x_i + b_k) p_{k-1}(x_i) + c_k p_{k-2}(x_i)
$$

ここで、[`reccurence_first_coef`](@ref) は `a_k` を、[`reccurence_second_coef`](@ref) は `b_k` を、[`reccurence_third_coef`](@ref) は `c_k` を、[`reccurence_deno_coef`](@ref) は `d_k` を与えます。
