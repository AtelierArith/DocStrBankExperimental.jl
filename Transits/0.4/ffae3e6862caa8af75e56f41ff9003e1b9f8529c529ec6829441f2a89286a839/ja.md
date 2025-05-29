```
IntegratedLimbDark(limbdark; N=21, basis=:legendre)
IntegratedLimbDark(u; kwargs...)
```

露出中間の時間平均フラックスを計算するために、リムダークニング法則 `limbdark` を数値積分スキームでラップします。各時間ステップ `t` に対して、`N` 個の追加ポイントが *スーパサンプリング* され、`t-texp/2` から `t+texp/2` までの範囲で時間平均フラックスが数値積分によって計算されます。

リムダークニング係数のセット `u` が提供されると、デフォルトで [`PolynomialLimbDark`](@ref) 法則が使用されます。

# 数学的形式

$$
\bar{F}(t) = \frac{1}{\Delta t}\int_{t-\Delta t / 2}^{t+\Delta t / 2}{F(t')dt'}
$$

ここで $F$ はラップされたリムダークニング法則であり、$\Delta t$ は露出時間です。

## 数値積分

積分は [ガウス数値積分](https://en.wikipedia.org/wiki/Gaussian_quadrature) によって近似されます。

$$
\frac{1}{\Delta t} \int{F(t')dt'} \approx \frac12\sum_i^N{w_i * F(\frac{\Delta t}{2}\xi_i + t)}
$$

ここで、重み `w_i` とノード `ξ_i` は与えられた数値積分ルールによって定義されます。ノードは、-1 から 1 の間で直交多項式を `N` 回評価することによって定義されます。直交多項式基底の自然な範囲 `-1, 1` から露出時間によって定義される範囲に移行するために必要な区間の変更に注意してください。

以下の基底は [FastGaussQuadrature.jl](https://github.com/JuliaApproximation/FastGaussQuadrature.jl) から利用可能です。さらに、`nodes, weights = f(N)` を計算する関数を渡すこともできます。

  * `:legendre` - 開区間 `(-1, 1)` のレジェンドル多項式基底
  * `:radau` - 半開区間 `[-1, 1)` のレジェンドル多項式基底
  * `:lobatto` - 閉区間 `[-1, 1]` のレジェンドル多項式基底

```
