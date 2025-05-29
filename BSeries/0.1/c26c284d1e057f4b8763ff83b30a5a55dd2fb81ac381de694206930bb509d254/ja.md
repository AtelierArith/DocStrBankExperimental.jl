```
modified_equation(series_integrator)
```

B系列を計算します。これは、B系列 `series_integrator` を用いた時間積分法の修正方程式のものです。

常微分方程式 (ODE) $u'(t) = f(u(t))$ とルンゲ・クッタ法を考えた場合、数値解を与えられた時間ステップサイズで修正ODE $u'(t) = fₕ(u(t))$ の正確な解として解釈するというアイデアがあります。このメソッドは、$h fₕ$ のB系列を返します。

!!! note "基本微分による正規化"
    このメソッドによって返されるB系列の係数は、時間ステップのべき乗を `symmetry` で割り、入力ベクトル場 $f$ の対応する基本微分で掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。


# 参考文献

以下の文献の3.2節

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
