```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    xvals::AbstractVector,
    initialpivots::AbstractVector=[1];
    kwargs...
) where {ValueType}
```

関数 $f(x)$ を量子テンソル列として補間します。これは1次元関数のオーバーロードです。引数と戻り値の型についての説明は、メインオーバーロードのドキュメントを参照してください。
