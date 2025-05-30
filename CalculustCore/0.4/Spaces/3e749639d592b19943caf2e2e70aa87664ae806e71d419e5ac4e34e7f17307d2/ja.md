```julia
laplaceOp(V, discr)

```

ガレルキン離散化の場合、負ラプラシアンのエントリは次のように与えられます。

$$
[A]_{ij} = \int_\Omega \nabla\phi_i(x) \cdot \nabla\phi_j(x) dx
$$

v,u ∈ H¹₀(Ω)

(v,-∇² u) = (vx,ux) + (vy,uy)

```
     := a(v,u)
```
