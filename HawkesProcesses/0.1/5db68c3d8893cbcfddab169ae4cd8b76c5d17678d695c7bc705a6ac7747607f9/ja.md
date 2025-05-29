```
simulate(bg::Number, kappa::Float64, kern::Function, maxT::Number)
```

0から`maxT`までのホークス過程を`bg`、`kappa`、`kern`のパラメータでシミュレートします。

# 引数

  * `bg`: ホークス過程の背景率。定数または正の関数。
  * `kappa`: ホークス過程のカッパパラメータ。
  * `kern` : ホークス過程のカーネル関数。
  * `maxT` : ホークス過程がシミュレートされる最大時間。

# 注意事項

  * kappaは安定したホークス過程のために0と1の間でなければなりません。

# 例

``julia kern_f(x) = pdf.(Distributions.Exponential(1/0.5), x)

simevents = simulate(0.5, 0.5, kern_f, 100) ``
