```
rnumber(symbols::Symbol)
rnumber(s::String)
```

Create symbolic rnumber.

# Expamples

```
julia> ps = rnumber(:a)
a

julia> rnumber("a") == ps
true
```
