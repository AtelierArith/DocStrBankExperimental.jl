```
GenomicInterval{T}(data)
```

The returned data is converted to GenomicInterval{T} if there is an implemented [`Base.convert`](https://docs.julialang.org/en/v1/base/base/#Base.convert) function for the type of data. This method provides a useful hook for converting custom types to GenomicInterval{T}.
