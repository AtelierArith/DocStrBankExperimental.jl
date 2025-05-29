```
geodesic(M::AbstractManifold, p, X, T::AbstractVector) -> AbstractVector
```

接地線 $γ_{p,X}: I → \mathcal M$ を評価します。ここで、$γ_{p,X}(0) = p$ かつ $\dot γ_{p,X}(0) = X$ であり、接地線はさらに次の条件を満たします。

$$
∇_{\dot γ_{p,X}(t)} \dot γ_{p,X}(t) = 0,
$$

時点 `t` は `T` から取られます。
