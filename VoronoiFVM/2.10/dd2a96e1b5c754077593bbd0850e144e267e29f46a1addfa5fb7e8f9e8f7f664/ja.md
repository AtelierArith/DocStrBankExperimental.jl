```julia
integrate(, coordl, coordr, hnormal, velofunc; kwargs...)

```

これは、$x_K$と$x_L$の間のエッジ$\sigma=\overline{\mathtt{coordl}\,\mathtt{coordr}}$に沿って`velofunc`を統合する内部関数です。ここで、$\mathtt{hnormal}=x_K-x_L$を使用して、[シンプソンのルール](https://en.wikipedia.org/wiki/Simpson%27s_rule)に従って正確に計算します。直交座標系に対して、$\int_{\sigma} \mathbf{v} \cdot \mathbf{n} \,\mathrm{ds} \lvert x_K - x_L \rvert / \lvert\sigma\rvert$を計算します。
