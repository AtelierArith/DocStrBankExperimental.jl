```
Wishart(ν, S)
```

```julia
ν::Real           自由度（整数または p - 1 より大きい実数）
S::AbstractPDMat  p x p スケール行列
```

[ウィシャート分布](http://en.wikipedia.org/wiki/Wishart_distribution)は、$p\times p$ の実数、正定値半定行列 $\mathbf{H}$ に対してガンマ分布を一般化します。

もし $\nu>p-1$ であれば、$\mathbf{H}\sim \textrm{W}_p(\nu, \mathbf{S})$ はランク $p$ を持ち、その確率密度関数は次のようになります。

$$
f(\mathbf{H};\nu,\mathbf{S}) = \frac{1}{2^{\nu p/2} \left|\mathbf{S}\right|^{\nu/2} \Gamma_p\left(\frac {\nu}{2}\right ) }{\left|\mathbf{H}\right|}^{(\nu-p-1)/2} e^{-(1/2)\operatorname{tr}(\mathbf{S}^{-1}\mathbf{H})}.
$$

もし $\nu\leq p-1$ であれば、$\mathbf{H}$ はランク $\nu$ であり、正定値行列の空間における適切に選ばれた体積要素に対して密度を持ちます。詳細は[こちら](https://doi.org/10.1214/aos/1176325375)を参照してください。

整数 $\nu$ の場合、次のように与えられるランダム行列

$$
\mathbf{H} = \mathbf{X}\mathbf{X}^{\rm{T}},
\quad\mathbf{X} \sim \textrm{MN}_{p,\nu}(\mathbf{0}, \mathbf{S}, \mathbf{I}_{\nu})
$$

は $\mathbf{H}\sim \textrm{W}_p(\nu, \mathbf{S})$ になります。非整数の $\nu$ の場合、ウィシャート行列は[Bartlett分解](https://en.wikipedia.org/wiki/Wishart_distribution#Bartlett_decomposition)を通じて生成できます。
