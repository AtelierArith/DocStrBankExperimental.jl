```
NonCentered()
```

`SparseVariationalApproximation`と一緒に使用されます。`SparseVariationalApproximation`の`q`フィールドは、`cholesky(cov(u)).L \ (u - mean(u))`に対する近似事後として解釈されるべきであり、ここで`u`は擬似点です。

これは「ホワイト化された」パラメータ化としても知られています[1]。

[`Centered`](@ref)も参照してください。

[1] - https://en.wikipedia.org/wiki/Whitening_transformation
