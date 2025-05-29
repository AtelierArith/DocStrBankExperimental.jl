```
durbin(r::AbstractVector)
```

`y = T \ (-r)` を計算します。ここで `T = SymmetricToeplitz(vcat(1, r[1:end-1]))` です。`T` は正定値であると仮定されています。`r` の長さは n です。
