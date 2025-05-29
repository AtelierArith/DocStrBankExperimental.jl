```
logdet(m::LinearMixedModel)
```

`log(det(Λ'Z'ZΛ + I)) + m.optsum.REML * log(det(LX*LX'))` をその場で評価して返します。

ここで、LXはブロック下部コレスキー因子における固定効果に対応する対角項です。
