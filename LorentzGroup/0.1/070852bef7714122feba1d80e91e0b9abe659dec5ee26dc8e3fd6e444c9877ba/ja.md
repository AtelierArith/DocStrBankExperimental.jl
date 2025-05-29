```
minkowskinormalize(u::AbstractVector)
```

ベクトル4ベクトル $u$ を正規化します。これはベクトルが零であるかどうかをチェックしないため、その場合、結果は発散するか `NaN` を含むことになります。
