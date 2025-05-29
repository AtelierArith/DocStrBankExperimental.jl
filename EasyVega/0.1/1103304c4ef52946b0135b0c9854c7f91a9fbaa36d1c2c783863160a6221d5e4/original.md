```
LinearScale(), LogScale(), PowScale(), SqrtScale(), SymlogScale(), TimeScale(), UtcScale(), 
SequentialScale(), OrdinalScale(), BandScale(), PointScale(), QuantileScale(), QuantizeScale(), 
ThresholdScale(), BinordinalScale()
```

Create a scale of a specific type. [Vega docs](https://vega.github.io/vega/docs/scales/)

# Examples

```julia
yscale = BandScale(range="height", domain=dat.y, domain_sort=true)
cscale = OrdinalScale(range="category", domain=dat.c)
```
