```
curve_fit(model, xdata, ydata, p0) -> fit
curve_fit(model, xdata, ydata, wt, p0) -> fit
```

非線形 `model` にデータをフィットさせます。`p0` は初期モデルパラメータの推測（例を参照）であり、`wt` はオプションの重みの配列です。返されるオブジェクトは合成型（`LsqFitResult`）で、いくつかの興味深い値を持っています：

  * `fit.resid` : 残差 = 残差のベクトル
  * `fit.jacobian` : 解における推定ヤコビアン

さらに、自由度を照会することも可能です：

  * `dof(fit)`
  * `coef(fit)`

## 例

```julia
# 二つのパラメータを持つ指数モデル
# x: 独立変数の配列
# p: モデルパラメータの配列
model(x, p) = p[1]*exp.(-x.*p[2])

# 一部の例データ
# xdata: 独立変数
# ydata: 従属変数
xdata = range(0, stop=10, length=20)
ydata = model(xdata, [1.0 2.0]) + 0.01*randn(length(xdata))
p0 = [0.5, 0.5]

fit = curve_fit(model, xdata, ydata, p0)
```
