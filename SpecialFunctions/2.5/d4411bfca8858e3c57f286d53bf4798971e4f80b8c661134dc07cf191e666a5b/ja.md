```
gamma(z)
```

複素数 $z$ に対するガンマ関数を計算します。定義は次の通りです。

$$
\Gamma(z)
:=
\begin{cases}
    n!
    & \text{のとき} \quad z = n+1 \;, n = 0,1,2,\dots
    \\
    \int_0^\infty t^{z-1} e^{-t} \, \mathrm{d}t
    & \text{のとき} \quad \Re(z) > 0
\end{cases}
$$

そして、全ての複素平面において解析的に続けられます。

# 例

```jldoctest
julia> gamma(0)
Inf

julia> gamma(1)
1.0

julia> gamma(2)
1.0

julia> gamma(0.5)^2 ≈ π
true

julia> gamma(4 + 1) == prod(1:4) == factorial(4)
true
```

外部リンク: [DLMF 5.2.1](https://dlmf.nist.gov/5.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Gamma_function).

参照: [`loggamma(z)`](@ref SpecialFunctions.loggamma) は $\log \Gamma(z)$ のため、[`gamma(a,z)`](@ref SpecialFunctions.gamma(::Number,::Number)) は上部不完全ガンマ関数 $\Gamma(a,z)$ のためです。

# 実装者

  * `Float`: C標準数学ライブラリ   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `Complex`: `exp(loggamma(z))` による。
  * `BigFloat`: 多倍長浮動小数点用のCライブラリ [MPFR](https://www.mpfr.org/)
