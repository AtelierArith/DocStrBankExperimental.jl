```
BiweightMidcovariance(; c=9.0, modify_sample_size=false)
```

バイウェイトミッド共分散は、外れ値に対して強靭な共分散推定量です。

この手法は元々天体物理学から派生したものであり[1]、Pythonモジュール[Astropy](https://www.astropy.org/) [2]やNISTのDataplot [3]に実装されています。

2つのランダム変数$x$と$y$を考え、$n$の観測値$\{(x_i, y_i)\}$があるとします。バイウェイトミッド共分散は次のように定義されます：

$$
n_s\cdot\frac{
    \sum_{|u_i|<1,|v_i|<1}(x_i - M_x)(1 - u_i^2)^2(y_i - M_y)(1 - v_i^2)^2
}{
    \left(\sum_{|u_i|<1}(1 - u_i^2)(1-5u_i^2)\right)
    \left(\sum_{|v_i|<1}(1 - v_i^2)(1-5v_i^2)\right)
}
$$

ここで、$n_s$はサンプルサイズ、$M_x$と$M_y$はそれぞれ$\{x_i\}$と$\{y_i\}$の中央値であり、

$$
\begin{aligned}
u_i &= \frac{x_i - M_x}{c \cdot \mathrm{MAD}_x} \\
v_i &= \frac{y_i - M_y}{c \cdot \mathrm{MAD}_y},
\end{aligned}
$$

ここで、$\mathrm{MAD}$は中央値絶対偏差を表します。

$$
\begin{aligned}
\mathrm{MAD}_x &= \mathrm{median}(\left\{\left|x_i - M_x\right|\right\}) \\
\mathrm{MAD}_y &= \mathrm{median}(\left\{\left|y_i - M_y\right|\right\}).
\end{aligned}
$$

もし$\mathrm{MAD}_x = 0$または$\mathrm{MAD}_y = 0$の場合、ペアワイズ共分散はゼロと定義されます。

パラメータ$c$は調整定数で、デフォルトは$9.0$です。大きな値は除外される外れ値の数を減少させます — すなわち、ロバスト性を減少させますが、サンプル効率を向上させます。

# フィールド

  * `c::Float64`: 上記の$c$に対応する調整定数。
  * `modify_sample_size::Bool`: `false`の場合、サンプルサイズ$n_s$は観測値の総数$n$に等しくなります。これは文献におけるバイウェイトミッド共分散の標準的な定義と一致します。それ以外の場合、分子では外れ値として拒否されない要素のみをカウントします。すなわち、$|u_i|<1$および$|v_i|<1$である要素です。これはastropy [2]の実装に従っています。

# 複雑さ

  * 空間: $O(p^2)$
  * 時間: $O(np^2)$

# 参考文献

[1] Beers, Flynn, and Gebhardt (1990; AJ 100, 32) "Measures of Location and Scale for Velocities in Clusters of Galaxies – A Robust Approach"

[2] [Astropy biweight_midcovariance](https://docs.astropy.org/en/stable/api/astropy.stats.biweight_midcovariance.html)

[3] [NIST Dataplot biweight midcovariance](https://www.itl.nist.gov/div898/software/dataplot/refman2/auxillar/biwmidc.htm)
