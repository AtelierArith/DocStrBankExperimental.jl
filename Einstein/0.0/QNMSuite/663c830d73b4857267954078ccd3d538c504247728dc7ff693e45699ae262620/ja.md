```
qnm_schw_expansion_dolan_ottewill(::Type{TF}, s::TI, l::TI, n::TI) where {TF<:AbstractFloat,TI<:Integer}
```

シュワルツシルトQNM周波数の高$\ell$漸近展開を、ドランとオッテウィルの方法を用いて計算します [Dolan:2009nk](@cite)。

QNM周波数は、逆数の冪の展開として書くことができます $L=\ell+\frac{1}{2}$

$$
\omega_{l n}=\varpi_{-1}^{(n)} L+\varpi_0^{(n)}+\varpi_1^{(n)} L^{-1}+\varpi_2^{(n)} L^{-2}+\ldots
$$

任意のスピン $\beta=1-s^2$ と任意のオーバートーン番号 $n$ に対する最も低い展開係数は次のように与えられます

$$
\begin{aligned}
& \sqrt{27} \varpi_{-1}^{(n)}=1 \\
& \sqrt{27} \varpi_0^{(n)}=-i N \\
& \sqrt{27} \varpi_1^{(n)}=\frac{\beta}{3}-\frac{5 N^2}{36}-\frac{115}{432} \\
& \sqrt{27} \varpi_2^{(n)}=-i N\left[\frac{\beta}{9}+\frac{235 N^2}{3888}-\frac{1415}{15552}\right] \\
& \sqrt{27} \varpi_3^{(n)}=-\frac{\beta^2}{27}+\frac{204 N^2+211}{3888} \beta+\frac{854160 N^4-1664760 N^2-776939}{40310784} \\
& \sqrt{27} \varpi_4^{(n)}=i N\left[\frac{\beta^2}{27}+\frac{1100 N^2-2719}{46656} \beta+\frac{11273136 N^4-52753800 N^2+66480535}{2902376448}\right]
\end{aligned}
$$

# 引数

  * `TF`: 浮動小数点数の型。
  * `s`: 関心のある場のスピン重み。
  * `l`: 関心のある多極数。
  * `n`: 関心のあるオーバートーン番号。

# 参考文献

  * [Dolan:2009nk](@cite)
  * [qnm/qnm/schwarzschild/approx.py at master · duetosymmetry/qnm](https://github.com/duetosymmetry/qnm/blob/master/qnm/schwarzschild/approx.py)

```
