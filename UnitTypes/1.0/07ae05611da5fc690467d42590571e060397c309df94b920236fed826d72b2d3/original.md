`macro makeDimension(dimName, measure)`

Make a new dimension `dimName` of `measure`; also creates 'Abstract`dimName`'

```     @makeDimension Diameter Meter 

```
d = Diameter(MilliMeter(3.4))
r = Radius(d)
```

```
