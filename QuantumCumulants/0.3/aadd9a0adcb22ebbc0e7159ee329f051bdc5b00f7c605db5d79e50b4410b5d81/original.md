```
cnumber(symbols::Symbol)
cnumber(s::String)
```

Create symbolic cnumber.

# Expamples

```
julia> ps = cnumber(:a)
a

julia> cnumber("a") == ps
true
```
