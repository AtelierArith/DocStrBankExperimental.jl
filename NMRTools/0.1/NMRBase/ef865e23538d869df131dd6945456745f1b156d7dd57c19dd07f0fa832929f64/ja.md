```
scale(d::AbstractNMRData)
```

データのスケーリングファクターを返します。これは、スキャンの数、受信ゲイン、および指定されている場合はサンプル濃度を組み合わせたものです。

$$
\mathrm{scale} = \mathrm{ns} \cdot \mathrm{rg} \cdot \mathrm{conc}
$$
