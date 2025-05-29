```
intdim(::LearnBase.ObsDimension)
```

Returns the integer associated to a dimension object  i.e. `intdim(ObsDim.Constant{3})`  returns `3`.  The function is designed to work on matices so  `intdim(::ObsDim.Last)` will return `2`.
