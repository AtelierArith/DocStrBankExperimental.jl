```
modify(m::AbstractModel, transforms...)
```

Modify a given `model` using the set of `transforms`. This is the most general function that allows you to apply a sequence of model transformation for example

```julia-repl
modify(Gaussian(), Stretch(2.0, 1.0), Rotate(π/4), Shift(1.0, 2.0), Renorm(2.0))
```

will create a asymmetric Gaussian with position angle `π/4` shifted to the position (1.0, 2.0) with a flux of 2 Jy. This is similar to Flux's chain.
