```
MomentumBasis(pmin, pmax, Npoints)
MomentumBasis(b::PositionBasis)
```

運動量空間における粒子の基底。

簡単のため、周期境界が仮定されており、これは `pmax` が基底に含まれないことを意味しますが、`pmin` と同じと定義されています。

[`PositionBasis`](@ref) が引数として与えられた場合、$p_{min}$ と $p_{max}$ の正確な値は周期境界条件によりほぼ任意であり、$-\pi/dx$ と $\pi/dx$ に選ばれます。ここで、$dx=(x_{max}-x_{min})/N$ です。
