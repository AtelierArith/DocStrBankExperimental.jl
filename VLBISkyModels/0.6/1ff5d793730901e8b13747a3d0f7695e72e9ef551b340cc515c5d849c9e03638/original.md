```
Stretch(α, β)
Stretch(r)
```

Stretched the model in the x and y directions, i.e. the new intensity is     Iₛ(x,y) = 1/(αβ) I(x/α, y/β), where were renormalize the intensity to preserve the models flux.

# Example

```julia-repl
julia> modify(Gaussian(), Stretch(2.0)) == stretched(Gaussian(), 2.0, 1.0)
true
```

If only a single argument is given it assumes the same stretch is applied in both direction.

```julia-repl
julia> Stretch(2.0) == Stretch(2.0, 2.0)
true
```
