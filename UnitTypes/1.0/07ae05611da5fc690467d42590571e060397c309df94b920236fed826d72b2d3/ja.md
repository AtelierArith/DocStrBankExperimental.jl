`macro makeDimension(dimName, measure)`

新しい次元 `dimName` を `measure` で作成します。また、'Abstract`dimName`' も作成します。

```@makeDimension Diameter Meter

```

d = Diameter(MilliMeter(3.4)) r = Radius(d)

```

```
