```
@lazy struct Foo
    a::Int
    @lazy b::Int
    @lazy c::Float64
end
```

Make a struct `Foo` with the lazy fields `b` and `c`.
