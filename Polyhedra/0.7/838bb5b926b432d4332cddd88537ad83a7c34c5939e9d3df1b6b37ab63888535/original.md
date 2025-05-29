```
struct Line{T, AT <: AbstractVector{T}}
    a::AT
end
```

The conic hull of `a` and `-a`, i.e. the set of points `λa` where `λ` is any real number.
