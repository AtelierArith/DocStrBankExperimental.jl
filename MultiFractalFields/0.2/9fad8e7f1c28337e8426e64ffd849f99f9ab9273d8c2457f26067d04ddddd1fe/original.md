```
Linear(ξ, [λ = 1], [σ² = 1])
```

Linear covariance function with scaling exponent `ξ`, correlation length `λ` and variance `σ²`.

It is defined as $C(r) = \begin{cases} \sigma^2 \left(1 - \displaystyle \left(\frac{r}{\lambda}\right)^{\xi}\right) & \text{if }r ≤ \lambda\\ 0 & \text{if }r>\lambda\end{cases}$.

# Examples

```jldoctest
julia> lincov = Linear(0.5, 1.5, 3)
Linear{Float64}(ξ=0.5, λ=1.5, σ²=3.0)

julia> lincov(0)
3.0

julia> lincov(1.5)
0.0
```
