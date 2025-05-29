```
radiationPower(md::MagneticDipole{FT}) where {FT<:Real}
```

計算放射功率。 $P_{rad} = ∫∫  U(θ, ϕ)sinθ  dθdϕ$ 對磁偶極子可直接在源縫表面積分： $P_{rad} = ∫∫ |E(r)|²/(2η₀) dxdy$
