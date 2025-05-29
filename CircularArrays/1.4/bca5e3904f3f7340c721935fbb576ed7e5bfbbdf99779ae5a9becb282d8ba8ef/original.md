```
CircularArray{T, N, A} <: AbstractArray{T, N}
```

`N`-dimensional array backed by an `AbstractArray{T, N}` of type `A` with fixed size and circular indexing.

```
array[index...] == array[mod1.(index, size)...]
```
