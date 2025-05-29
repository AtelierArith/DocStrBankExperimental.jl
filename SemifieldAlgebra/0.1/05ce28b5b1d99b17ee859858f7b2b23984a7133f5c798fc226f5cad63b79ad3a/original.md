```
struct Semifield{T,A,M,MI,Z,O} <: Number
    val::T
end
```

`T` is the value type, `A` is the addition function, `M` is the multiplication function, `MI` is the muliplication inverse function, `Z` is the zero element function and `O` is the one element function.
