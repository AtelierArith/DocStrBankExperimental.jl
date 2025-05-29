```
plan_idct(A [, dims [, flags [, timelimit [, num_threads]]]])
```

最適化された逆離散コサイン変換（DCT）を事前に計画します。これは[`plan_fft`](@ref)に似ていますが、[`idct`](@ref)を計算する関数を生成します。最初の2つの引数は[`idct`](@ref)と同じ意味を持ちます。
