```
example_constraints(X::AbstractUncertainIndexValueDataset, 
    Y::AbstractUncertainIndexValueDataset;
    d_xinds = Uniform(0.5, 1.1), d_yinds = Uniform(0.9, 1.7),
    d_xvals = Uniform(0.05, 0.15), d_yvals = Uniform(0.3, 0.4))
```

2つの不確実なインデックス値データセット `X` と `Y` のインデックスと値を制約するために使用できるランダムサンプリング制約のセットを生成します。制約は次のように生成されます：

  * `constraints_inds_x = TruncateStd(rand(d_xinds))`
  * `constraints_inds_y = TruncateStd(rand(d_yinds))`
  * `constraints_vals_x = [TruncateQuantiles(0.5 - rand(d_xvals), 0.5 + rand(d_xvals)) for i = 1:length(X)]`
  * `constraints_vals_y = [TruncateQuantiles(0.5 - rand(d_yvals), 0.5 + rand(d_yvals)) for i = 1:length(Y)]`

タプルのタプル `((constraints_inds_x, constraints_vals_x), (constraints_inds_y, constraints_vals_y))` を返します。
