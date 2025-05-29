```
gausslaguerre(n::Integer, α::Real) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of generalized [Gauss-Laguerre quadrature](https://en.wikipedia.org/wiki/Gauss%E2%80%93Laguerre_quadrature).

$$
\int_{0}^{+\infty} f(x) x^\alpha e^{-x} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# Examples

```jldoctest
julia> x, w = gausslaguerre(3, 1.0);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 120
true
```

Optionally, a reduced quadrature rule can be computed. In that case, only those points and weights are computed for which the weight does not underflow in the floating point precision type. Supply the optional argument `reduced = true`.

Though the code is generic, heuristical choices on the choice of the algorithm are based on achieving machine precision accuracy only for `Float64` type. In case the default choice of algorithm does not achieve the desired accuracy, the user can manually invoke the following routines:

  * `gausslaguerre_GW`: computation based on Golub-Welsch
  * `gausslaguerre_rec`: computation based on Newton iterations applied to evaluation  using the recurrence relation
  * `gausslaguerre_asy`: the asymptotic expansions
