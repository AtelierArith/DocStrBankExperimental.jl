```
modifying_integrator(series_integrator)
```

B系列 `series_integrator` を用いた時間積分法の「修正積分器」方程式のB系列を計算します。

常微分方程式 (ODE) $u'(t) = f(u(t))$ とルンゲ・クッタ法を考えたとき、目的は修正されたODE $u'(t) = fₕ(u(t))$ を見つけることです。この修正されたODEに対して、与えられた時間ステップサイズでの数値解が元のODEの正確な解となるようにします。このメソッドは $h fₕ$ のB系列を返します。

!!! note "基本微分による正規化"
    このメソッドによって返されるB系列の係数は、時間ステップのべき乗を `symmetry` で割り、入力ベクトル場 $f$ の対応する基本微分で掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。


# 参考文献

以下の文献の3.2節

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
