```
solve_maxwell(J::NTuple{3,Polynomial{3,T}};ϵ=1,μ=1,ω=1)
```

Compute a pair of vectors of polynomials `E` and `H` satisfying the Maxwell system:

$$
\begin{aligned}
  \mathrm{i}\omega\varepsilon\boldsymbol{E} + \operatorname{rot} \boldsymbol{H} &= \boldsymbol{J}, \qquad &
  -\mathrm{i}\omega\mu\boldsymbol{H} + \operatorname{rot}\boldsymbol{E} &= \boldsymbol{0}, \\
  \varepsilon\operatorname{div}\boldsymbol{E} &= \rho, &
  \mu\operatorname{div}\boldsymbol{H} &= 0,
\end{aligned}
$$

with the sources being constrained by the charge conservation equation:

$$
\begin{aligned}
  \operatorname{div}\boldsymbol{J} - \mathrm{i}\omega\rho &= 0.
\end{aligned}
$$

Returns the pair `(E, H)`.

# Examples

```jldoctest
julia> J = (Polynomial((0,2,1) => 1), Polynomial((0,1,1) => 1), Polynomial((1,0,1) => 1))
(y²z, yz, xz)

julia> E, H = solve_maxwell(J);

julia> E
((-0.0 - 1.0im) + (0.0 + 2.0im)z + (-0.0 - 1.0im)y²z, (-0.0 - 1.0im)yz, (-0.0 - 1.0im) + (-0.0 - 1.0im)xz)

julia> H
(y, 2.0 + z - y², 2.0yz)
```
