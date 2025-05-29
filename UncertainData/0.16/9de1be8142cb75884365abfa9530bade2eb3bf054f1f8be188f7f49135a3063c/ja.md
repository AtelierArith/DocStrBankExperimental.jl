```
example_constraints(X::AbstractUncertainIndexValueDataset, 
    d_xinds = Uniform(0.5, 1.1), d_yinds = Uniform(0.9, 1.7))
```

不確実なインデックス値データセット `X` のインデックスと値を制約するために使用できるランダムサンプリング制約のセットを生成します。これらは次のように生成されます：

  * `constraints_inds = TruncateStd(rand(d_xinds))`
  * `constraints_vals = [TruncateQuantiles(0.5 - rand(d_xvals), 0.5 + rand(d_xvals)) for i = 1:length(X)];`

タプル (constraints*inds, constraints*vals) を返します。
