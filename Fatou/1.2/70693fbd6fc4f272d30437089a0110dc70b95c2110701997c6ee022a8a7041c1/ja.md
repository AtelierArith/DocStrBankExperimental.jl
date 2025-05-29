```
basin(::Fatou.Define, ::Integer)
```

`Fatou.Define`の`j`-番目の流域をLaTeX形式で出力します。ニュートン-ラフソン法の各反復は、より複雑な集合を生成します。

# 例

```Julia
julia> basin(newton("z^3-1"),2)
L"$\displaystyle D_2(\epsilon) = \left\{z\in\mathbb{C}:\left|\,z - \frac{\left(z - \frac{z^{3} - 1}{3 z^{2}}\right)^{3} - 1}{3 \left(z - \frac{z^{3} - 1}{3 z^{2}}\right)^{2}} - \frac{z^{3} - 1}{3 z^{2}} - r_i\,\right|<\epsilon,\,\forall r_i(\,f(r_i)=0 )\right\}$"
```
