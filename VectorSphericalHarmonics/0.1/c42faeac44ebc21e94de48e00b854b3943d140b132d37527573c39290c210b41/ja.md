```
Hansen <: AbstractVSH
```

Hansenベクトル球面調和関数 $\mathbf{H}_{J M}^{(\lambda)}\left(\hat{n}\right)$ は、[`Irreducible`](@ref) 調和関数を通じて関連しています。

$$
\begin{aligned}
\mathbf{H}_{JM}^{\left(-1\right)}\left(\hat{n}\right) & =-\sqrt{\frac{J+1}{2J+1}}\mathbf{Y}_{JM}^{J+1}\left(\hat{n}\right)+\sqrt{\frac{J}{2J+1}}\mathbf{Y}_{JM}^{J-1}\left(\hat{n}\right),\\
\mathbf{H}_{JM}^{\left(0\right)}\left(\hat{n}\right) & =\mathbf{Y}_{JM}^{J}\left(\hat{n}\right),\\
\mathbf{H}_{JM}^{\left(1\right)}\left(\hat{n}\right) & =\sqrt{\frac{J}{2J+1}}\mathbf{Y}_{JM}^{J+1}\left(\hat{n}\right)+\sqrt{\frac{J+1}{2J+1}}\mathbf{Y}_{JM}^{J-1}\left(\hat{n}\right),
\end{aligned}
$$
