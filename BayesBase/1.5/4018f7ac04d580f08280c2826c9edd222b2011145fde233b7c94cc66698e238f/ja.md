```
logpdf_sampling_optimized(d)
```

`logpdf_sample_optimized` 関数は、分布 `d` を入力として受け取り、対応する最適化された2つのバージョンを返します。これらはそれぞれ `logpdf()` を取得するためのものと、`rand!` でサンプリングするためのものです。`(logpdf_optimized(d), sampling_optimized(d))` のエイリアスですが、特化することもできます。
