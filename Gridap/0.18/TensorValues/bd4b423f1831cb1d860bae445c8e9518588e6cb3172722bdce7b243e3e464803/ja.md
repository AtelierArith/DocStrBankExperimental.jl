```
tr(v::MultiValue{Tuple{D,D,D2}}) -> ::VectorValue{D2}
```

最初の2つのインデックスで計算されたトレースの長さ `D2` のベクトルを返します: `resⱼ = Σᵢ vᵢᵢⱼ`.
