```
trace(b::Blob)
```

ブロブの位置トレースを取得します。`tm = Matrix(t::Trace)`を使用してN×2の行列を取得します。`tm = replace(Float64.(tm), 0=>NaN)`を使用して、欠測値があった場所にNaNを持つ行列を作成します。これは、欠測値があった場所にギャップを作成するため、プロットに便利です。
