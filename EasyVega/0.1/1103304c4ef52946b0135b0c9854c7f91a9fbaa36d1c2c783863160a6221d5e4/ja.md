```
LinearScale(), LogScale(), PowScale(), SqrtScale(), SymlogScale(), TimeScale(), UtcScale(), 
SequentialScale(), OrdinalScale(), BandScale(), PointScale(), QuantileScale(), QuantizeScale(), 
ThresholdScale(), BinordinalScale()
```

特定のタイプのスケールを作成します。[Vega docs](https://vega.github.io/vega/docs/scales/)

# 例

```julia
yscale = BandScale(range="height", domain=dat.y, domain_sort=true)
cscale = OrdinalScale(range="category", domain=dat.c)
```
