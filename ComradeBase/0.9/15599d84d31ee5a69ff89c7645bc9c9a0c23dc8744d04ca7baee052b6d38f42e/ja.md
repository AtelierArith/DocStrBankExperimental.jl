```
logclosure_amplitude(model, p1, p2, p3, p4)
```

モデル `m` のログクローズアミプリチュードを uv-四角形 u1,v1 -> u2,v2 -> u3,v3 -> u4,v4 で計算します。式は次の通りです。

$$
C = \log\left|\frac{V(u1,v1)V(u2,v2)}{V(u3,v3)V(u4,v4)}\right|
$$

三角形の数にわたってログクローズアミプリチュードマップを計算したい場合は、`logclosure_amplitudemap` 関数の使用を検討してください。
