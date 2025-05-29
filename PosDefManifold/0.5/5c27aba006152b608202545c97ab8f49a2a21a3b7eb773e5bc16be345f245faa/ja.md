```julia
    midrange(metric::Metric, P::ℍ{T}, Q::ℍ{T}) where T<:RealOrComplex
```

正定行列 $P$ と $Q$ の極値の平均であるミッドレンジ。サポートされているのはフィッシャー計量のみで、いわゆる*幾何学的ミッドレンジ*を可能にします。これはMostajeran et *al.* (2019) [🎓](@ref) で次のように定義されています。

$$
P * Q = \frac{1}{\sqrt{\lambda_(min)}+\sqrt{\lambda_(max)}}\Big(Q+\sqrt{\lambda_(min)*\lambda_(max)}P\Big)
$$

,

ここで、$\lambda_(min)$ と $\lambda_(max)$ は $P$ と $Q$ の極値一般化固有値です。

**例**

```julia
P=randP(3)
Q=randP(3)
M=midrange(Fisher, P, Q)
```
