```
PB <: AbstractVSH
```

Phinney-Burridge vector spherical harmonics $\mathbf{P}_{J M}^\gamma\left(\hat{n}\right)$ that are related to the [`Hansen`](@ref) harmonics through

$$
\begin{aligned}
\mathbf{P}_{JM}^{+1}\left(\hat{n}\right) & =\frac{1}{\sqrt{2}}\left(\mathbf{H}_{JM}^{\left(1\right)}\left(\hat{n}\right)-\mathbf{H}_{JM}^{\left(0\right)}\left(\hat{n}\right)\right),\\
\mathbf{P}_{JM}^{0}\left(\hat{n}\right) & =\mathbf{H}_{JM}^{\left(-1\right)}\left(\hat{n}\right),\\
\mathbf{P}_{JM}^{-1}\left(\hat{n}\right) & =\frac{1}{\sqrt{2}}\left(\mathbf{H}_{JM}^{\left(1\right)}\left(\hat{n}\right)+\mathbf{H}_{JM}^{\left(0\right)}\left(\hat{n}\right)\right).
\end{aligned}
$$
