```
plot_evals(evals; f, ylabel="情報量")
```

サブセットの実験に対して評価されたパフォーマンス指標を視覚化するスティックプロットを作成します。

引数 `evals` は [`evaluate_experiments`](@ref CEEDesigns.StaticDesigns.evaluate_experiments) の出力である必要があり、kwarg `f`（提供されている場合）は `evals` を入力として受け取り、x軸にプロットされる順序でそのキーのリストを返す関数です。デフォルトでは、長さでソートされています。
