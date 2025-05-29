```
PositionBasis(xmin, xmax, Npoints)
PositionBasis(b::MomentumBasis)
```

実空間における粒子の基底。

簡単のため、周期境界が仮定されており、これは `xmax` によって定義される最も右の点が基底に含まれず、`xmin` と同じであると定義されることを意味します。

[`MomentumBasis`](@ref) が引数として与えられると、周期境界条件により $x_{min}$ と $x_{max}$ の正確な値はほぼ任意であり、$-\pi/dp$ と $\pi/dp$ に選ばれます。ここで、$dp=(p_{max}-p_{min})/N$ です。
