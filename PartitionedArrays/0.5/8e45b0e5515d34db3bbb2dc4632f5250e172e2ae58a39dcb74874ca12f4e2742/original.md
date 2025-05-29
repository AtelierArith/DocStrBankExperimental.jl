```
struct JaggedArray{T,Ti}
```

Efficient implementation of a vector of vectors. The inner vectors are stored one after the other in consecutive memory locations using an auxiliary vector `data`. The range of indices corresponding to each inner vector are encoded using a vector of integers `ptrs`.

# Properties

```
data::Vector{T}
ptrs::Vector{Ti}
```

Given `a::JaggedArray`, `a.data` contains the inner vectors. The `i`-th inner vector is stored in the range `a.ptrs[i]:(a.ptrs[i+1]-1)`. The number of inner vectors (i.e. `length(a)`) is `length(a.ptrs)-1`. `a[i]` returns a view of `a.data` restricted to the range `a.ptrs[i]:(a.ptrs[i+1]-1)`.

# Supertype hierarchy

```
JaggedArray{T,Ti} <: AbstractVector{V}
```

Given `a::JaggedArray`, `V` is `typeof(view(a.data,a.ptrs[i]:(a.ptrs[i+1]-1)))`.
