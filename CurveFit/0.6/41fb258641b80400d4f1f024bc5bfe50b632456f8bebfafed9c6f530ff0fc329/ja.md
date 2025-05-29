# `curve_fit`によって作成されたオブジェクトを使用して値を推定する

`call`メソッドはオーバーロードされているため、フィットオブジェクトを関数として使用できます：

## 例：

x = 1.0:10.0 @. y = 2*x + 1 + randn()

fit = curve_fit(LinearFit, x, y)

y1 = fit(5.1) y2 = apply_fit(fit, 5.1)
