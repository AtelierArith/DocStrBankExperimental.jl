```
Rotate(ξ)
```

Type for the rotated model. This is more fine grained constrol of rotated model.

# Example

```julia-repl
julia> modify(Gaussian(), Rotate(2.0)) == rotated(Gaussian(), 2.0)
true
```
