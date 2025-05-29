```
Periodogram(timeseries, Δ)
```

提供された時系列の周期グラムをサンプリングレート Δ で計算します。

# 引数

  * `timeseries`: 単変量の場合は `Vector`、多変量の場合は `n` 行 `d` 列の `Matrix` で、ここで `n` は観測数、`d` は時系列の次元です。
  * `Δ`: 正の実数。

周期グラムは次のように定義されます。

$$
\boldsymbol I(ω)&=\boldsymbol J(ω) \boldsymbol J(ω)^H \quad \text{where} \quad \boldsymbol J(ω) = \sqrt{\frac{Δ}{2π n}}\sum_{t=0}^{n-1} \boldsymbol{P}_{tΔ}e^{-itΔ ω}
$$

ここで、周期グラムは角周波数の観点から定義されており、正規化 $Δ/2π$ を使用しています。正規化の選択は本質的に任意ですが、これはスペクトル密度関数の定義と一致します。
