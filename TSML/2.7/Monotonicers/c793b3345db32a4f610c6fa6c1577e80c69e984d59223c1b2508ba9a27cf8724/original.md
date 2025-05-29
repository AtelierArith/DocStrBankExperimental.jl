```
transform!(st::Monotonicer, features::T) where {T<:Union{Vector,Matrix,DataFrame}}
```

Normalize monotonic or daily monotonic data by taking the diffs and counting the flips.
