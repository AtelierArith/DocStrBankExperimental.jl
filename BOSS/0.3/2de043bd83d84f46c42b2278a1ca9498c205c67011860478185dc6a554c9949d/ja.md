```
PlotOptions(Plots; kwargs...)
```

`PlotOptions`が`BossOptions`に`callback`として渡されると、最適化問題の状態が各イテレーションでプロットされます。1次元の`x`ドメインでのみ機能しますが、複数次元の`y`をサポートしています。

# 引数

  * `Plots::Module`: `using Plots`を評価し、`Plots`モジュールを`PlotsOptions`に渡します。

# キーワード

  * `f_true::Union{Nothing, Function}`: プロットされる真の目的関数。
  * `points::Int`: 各プロットされた関数のポイント数。
  * `xaxis::Symbol`: x軸のスケールを変更するために使用されます（`:identity`, `:log`）。
  * `yaxis::Symbol`: y軸のスケールを変更するために使用されます（`:identity`, `:log`）。
  * `title::String`: プロットのタイトル。
