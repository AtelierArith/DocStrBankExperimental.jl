```
sysi = innovation_form(sys, K)
```

システムを取得します

```
x' = Ax + Bu + Kv
y  = Cx + Du + v
```

そして、次のシステムを返します

```
x' = Ax + Kv
y  = Cx + v
```

ここで `v` はイノベーションシーケンスです。

Stochastic Control, Chapter 4, Åström を参照してください。
