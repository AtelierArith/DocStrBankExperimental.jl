```
KeyedDistribution(d::Distribution)
```

指定された `size(d)` に一致するパラメータのキーと次元名を使用して [`KeyedDistribution`](@ref) を構築します。パラメータにキーがない場合は、各次元の長さ `n` に対して `1:n` を使用します。
