```
generateGaussians(d::Integer, k::Integer, diagonal::Bool)
```

次元 `d` の `k` 個のガウス分布の平均と共分散を生成します。

`diagonal` は球状の場合は真、一般的な共分散行列の場合は偽である必要があります。
