````
colocalize_all(xs, ys; windowsize=3)

すべてのコロケーションメトリックを適用します。辞書を返すので、結果はresults[metric]に格納されます。
マルチスレッドで実行されます。
```julia
xs = rand(10, 10)
ys = rand(10, 10)
res =colocalize_all(xs, ys)
correlation_values = res["pearson"]
μ, md, σ, min, max, q1, q3, iqr, q95, q99, nans = describe_map(correlation_values)
```
````
