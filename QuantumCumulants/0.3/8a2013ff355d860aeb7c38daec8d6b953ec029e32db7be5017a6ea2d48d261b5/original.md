```
rnumbers(symbols::Symbol...)
rnumbers(s::String)
```

Create symbolic rnumbers.

# Expamples

```
julia> ps = rnumbers(:a, :b)
(a, b)

julia> rnumbers("a b") == ps
true
```
