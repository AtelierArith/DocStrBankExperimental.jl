```
mapobs(namedfs::NamedTuple, data)
```

Map a `NamedTuple` of functions over `data`, turning it into a data container of `NamedTuple`s. Field syntax can be used to select a column of the resulting data container.

```julia
data = 1:10
nameddata = mapobs((x = sqrt, y = log), data)
getobs(nameddata, 10) == (x = sqrt(10), y = log(10))
getobs(nameddata.x, 10) == sqrt(10)
```
