```
compute_drt(ω_exp,Z_exp;ppd,showplot,rtol,regularization)
```

入力EISデータからDRTを計算するためのメイン関数。

# 属性

  * `ω_exp`: 入力EIS周波数
  * `Z_exp`: 入力EISインピーダンス
  * `ppd=7`: DRT計算のための出力τ範囲におけるデシデータポイント数
  * `showplot=false`: DRT結果をプロットするかどうか
  * `rtol=1e-03`: 希望する相対許容誤差。この値を超えるフィット結果が出た場合、関数は警告を出します
  * `regularization=false`: 正則化手法を使用するかどうか

# 例

```julia
using EISAnalysis, Statistics
eval(initialize())
ω_exp, Z_exp = (r/q).ω, (r/q).Z #これを実際のデータに置き換えてください
fit = compute_drt(ω_exp,Z_exp;showplot = false,regularization = true)
```
