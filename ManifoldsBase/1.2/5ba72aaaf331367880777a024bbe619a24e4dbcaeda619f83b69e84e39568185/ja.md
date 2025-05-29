```
geodesic(M::AbstractManifold, p, X, t::Real)
```

評価する測地線 $γ_{p,X}: I → \mathcal M$ は、$γ_{p,X}(0) = p$ かつ $\dot γ_{p,X}(0) = X$ であり、測地線はさらに次の条件を満たします。

$$
∇_{\dot γ_{p,X}(t)} \dot γ_{p,X}(t) = 0,
$$

時刻 `t` において。
