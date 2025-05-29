```
Oscillator{T<:Float64}
```

Custom type to represent a SDOF oscillator. The type has two fields:

  * `f_n` is the natural frequency of the oscillator
  * `ζ_n` is the damping ratio

# Examples

```julia-repl
    sdof = Oscillator( 1.0, 0.05 )
```
