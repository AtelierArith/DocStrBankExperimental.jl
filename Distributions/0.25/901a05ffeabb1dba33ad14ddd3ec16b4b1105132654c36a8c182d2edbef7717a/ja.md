```
StudentizedRange(ν, k)
```

*studentized range distribution* の確率密度関数は次のようになります：

$$
f(q; k, \nu) = \frac{\sqrt{2\pi}k(k - 1)\nu^{\nu/2}}{\Gamma{\left(\frac{\nu}{2}\right)}2^{\nu/2 - 1}} \int_{0}^{\infty} {x^{\nu}\phi(\sqrt{\nu}x)} \left[\int_{-\infty}^{\infty} {\phi(u)\phi(u - qx)[\Phi(u) - \Phi(u - qx)]^{k - 2}}du\right]dx
$$

ここで

$$
\begin{aligned}
\Phi(x) &= \frac{1 + erf(\frac{x}{\sqrt{2}})}{2} &&(\text{正規分布のCDF})\\
\phi(x) &= \Phi'(x) &&(\text{正規分布のPDF})
\end{aligned}
$$

```julia
StudentizedRange(ν, k)     # パラメータ ν と k を持つ Studentized Range Distribution

params(d)        # パラメータを取得します。すなわち (ν, k)
```

外部リンク

  * [Studentized range distribution on Wikipedia](http://en.wikipedia.org/wiki/Studentized_range_distribution)
