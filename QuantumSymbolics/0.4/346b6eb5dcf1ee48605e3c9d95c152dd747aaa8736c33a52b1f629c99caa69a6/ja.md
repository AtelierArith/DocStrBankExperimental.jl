単一量子ビットパウリノイズCPTPマップ

```jldoctest
julia> apply!(express(Z1), [1], express(PauliNoiseCPTP(1/4,1/4,1/4)))
Operator(dim=2x2)
  basis: Spin(1/2)
 0.5+0.0im  0.0+0.0im
 0.0+0.0im  0.5+0.0im
```
