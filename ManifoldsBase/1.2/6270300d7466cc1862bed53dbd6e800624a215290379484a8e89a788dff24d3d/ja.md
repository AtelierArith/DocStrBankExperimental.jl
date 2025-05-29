```
parallel_transport_direction(M::AbstractManifold, p, X, d)
```

$$
X
$$

の平行輸送を曲線$c(t) = γ_{p,X}(t)$に沿って計算します。ここで$c(1)=q$であり、$c(t)=γ_{p,X}(t)$は$γ_{p,d}(0)=p$から方向$̇\dot γ_{p,d}(0)=d$に向かう唯一の測地線です。

デフォルトでは、この関数は[`parallel_transport_to`](@ref)`(M, p, X, q)`を呼び出します。ここで$q=\exp_pX$です。 ```
