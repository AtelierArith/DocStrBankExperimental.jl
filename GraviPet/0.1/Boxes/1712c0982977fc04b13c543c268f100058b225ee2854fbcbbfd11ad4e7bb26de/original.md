```
Box{D,T}(first::SVector{D}, last::SVector{D})
Box(first::SVector{D}, last::SVector{D})
```

Create a box domain with the specified lower and upper bounds. The bounds are given as vectors, and (some of) their elements can be infinity. The constraint `first < last` must hold in each dimension.
