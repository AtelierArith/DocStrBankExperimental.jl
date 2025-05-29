```
cnumbers(symbols::Symbol...)
cnumbers(s::String)
```

Create symbolic cnumbers.

# Expamples

```
julia> ps = cnumbers(:a, :b)
(a, b)

julia> cnumbers("a b") == ps
true
```
