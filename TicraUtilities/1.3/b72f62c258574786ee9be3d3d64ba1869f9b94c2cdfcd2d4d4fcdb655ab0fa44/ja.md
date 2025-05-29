```
get_qsmns(s::SPHQPartition)
```

オフセット配列 `qsmns::OffsetArray{ComplexF64, 3}` を返します。この配列には Q 係数が含まれており、exp(jωt) 時間変化を仮定し、Ticra 正規化規約を使用しています。配列の軸は `(1:2, -mmax:mmax, 1:nmax)` であり、つまり、いくつかのエントリ（`n < abs(m)` のもの）は常にゼロです。
