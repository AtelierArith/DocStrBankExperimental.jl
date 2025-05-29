```
q = exp(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},CanonicalMetric}, p, X)
exp!(M::MetricManifold{ℝ,<:Stiefel{<:Any,ℝ},CanonicalMetric}, q, p, X)
```

[`Stiefel`](@ref)`(n, k)`多様体上の[`CanonicalMetric`](@ref)に関する指数写像を計算します。

まず、接ベクトル$X$を点$p$に関してその水平成分と垂直成分に分解します。すなわち、

$$
X = pp^{\mathrm{T}}X + (I_n-pp^{\mathrm{T}})X,
$$

ここで$I_n$は$n×n$の単位行列です。$A=p^{\mathrm{T}}X$とし、垂直成分の`qr`分解を用いて$QR = (I_n-pp^{\mathrm{T}})X$とします。次に、行列指数$\operatorname{Exp}$を用いて$B$と$C$を次のように定義します。

$$
\begin{pmatrix}
B\\C
\end{pmatrix}
\coloneqq
\operatorname{Exp}\left(
\begin{pmatrix}
A & -R^{\mathrm{T}}\\ R & 0
\end{pmatrix}
\right)
\begin{pmatrix}I_k\\0\end{pmatrix}
$$

指数写像は次のように表されます。

$$
q = \exp_p X = pC + QB.
$$

詳細については、[EdelmanAriasSmith:1998](@cite)[Zimmermann:2017](@cite)を参照してください。 ```
