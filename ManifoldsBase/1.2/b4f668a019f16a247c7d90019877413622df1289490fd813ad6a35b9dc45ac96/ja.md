```
sectional_curvature(M::AbstractManifold, p, X, Y)
```

多様体 $\mathcal M$ の点 $p \in \mathcal M$ における二つの線形独立な接ベクトルに対する断面曲率を計算します。式は次のようになります。

$$

    \kappa_p(X, Y) = \frac{⟨R(X, Y, Y), X⟩_p}{\lVert X \rVert^2_p \lVert Y \rVert^2_p - ⟨X, Y⟩^2_p}

$$

ここで $R(X, Y, Y)$ は $\mathcal M$ 上の [`riemann_tensor`](@ref) です。

# 入力

  * `M`:   多様体 $\mathcal M$
  * `p`:   点 $p \in \mathcal M$
  * `X`:   接ベクトル $X \in T_p \mathcal M$
  * `Y`:   接ベクトル $Y \in T_p \mathcal M$

```
