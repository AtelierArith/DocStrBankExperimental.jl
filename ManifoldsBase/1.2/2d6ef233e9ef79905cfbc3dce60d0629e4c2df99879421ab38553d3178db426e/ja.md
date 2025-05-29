```
geodesic!(M::AbstractManifold, Q, p, X, T::AbstractVector) -> AbstractVector
```

初期点 `p` と速度 `X` を持つ [`AbstractManifold`](@ref) `M` 上の測地線を取得します。測地線は加速度がゼロの曲線です。すなわち、曲線 $γ_{p,X}: I → \mathcal M$ に対して、$γ_{p,X}(0) = p$ および $\dot γ_{p,X}(0) = X$ である測地線はさらに次の条件を満たします。

$$
∇_{\dot γ_{p,X}(t)} \dot γ_{p,X}(t) = 0,
$$

すなわち、この曲線はリーマン計量に関して加速度がゼロです。この関数は、`Q` の代わりに `T` からの時間点 `t` で測地線を評価します。
