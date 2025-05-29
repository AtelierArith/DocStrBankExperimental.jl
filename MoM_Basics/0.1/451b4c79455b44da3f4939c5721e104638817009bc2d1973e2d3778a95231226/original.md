```
radiationPower(md::MagneticDipole{FT}) where {FT<:Real}
```

计算辐射功率。 $P_{rad} = ∫∫  U(θ, ϕ)sinθ  dθdϕ$ 对磁偶极子可直接在源缝表面积分： $P_{rad} = ∫∫ |E(r)|²/(2η₀) dxdy$
