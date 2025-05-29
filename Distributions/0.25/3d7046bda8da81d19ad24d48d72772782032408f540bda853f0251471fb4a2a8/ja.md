```
LKJ(d, η)
```

```julia
d::Int   次元
η::Real  正の形状
```

[LKJ](https://doi.org/10.1016/j.jmva.2009.04.008) 分布は $d\times d$ 実相関行列（対角に1がある正定値行列）に対する分布です。もし $\mathbf{R}\sim \textrm{LKJ}_{d}(\eta)$ であれば、その確率密度関数は次のようになります。

$$
f(\mathbf{R};\eta) = \left[\prod_{k=1}^{d-1}\pi^{\frac{k}{2}}
\frac{\Gamma\left(\eta+\frac{d-1-k}{2}\right)}{\Gamma\left(\eta+\frac{d-1}{2}\right)}\right]^{-1}
|\mathbf{R}|^{\eta-1}.
$$

もし $\eta = 1$ であれば、LKJ分布は [相関行列の空間](https://www.jstor.org/stable/2684832) 上で一様です。

!!! note
    相関行列のコレスキー因子が必要な場合は、行列の因子分解を避ける [`LKJCholesky`](@ref) を使用する方が効率的です。

