```
struct Ray{T, AT <: AbstractVector{T}}
    a::AT
end
```

The conic hull of `a`, i.e. the set of points `λa` where `λ` is any nonnegative real number.
