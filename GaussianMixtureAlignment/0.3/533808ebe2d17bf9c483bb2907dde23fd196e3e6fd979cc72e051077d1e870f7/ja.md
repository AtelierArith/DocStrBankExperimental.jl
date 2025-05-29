```
score, tform, nevals = rocs_align_gmms(gmmfixed, gmmmoving; maxevals=1000)
```

与えられた2つのGMM間の最適なアライメントを、[ROCSアライメントアルゴリズム](https://docs.eyesopen.com/applications/rocs/theory/shape_shape.html)に基づいて、立体多極子を使用して見つけます。
