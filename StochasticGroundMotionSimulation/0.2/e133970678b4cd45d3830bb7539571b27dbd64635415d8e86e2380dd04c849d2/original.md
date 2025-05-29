```
transfer(f::Vector{T}, sdof::Oscillator) where T<:Real
```

Computes the modulus of the transfer function of a SDOF for a vector of frequencies

  * `f::Vector` is the vector of frequencies
  * `sdof::Oscillator` is the oscillator instance

# Examples

```julia-repl
  f = collect(range(0.1, stop=10.0, step=0.01))
  sdof = Oscillator(1.0)
  Hf = transfer(f, sdof)
```
