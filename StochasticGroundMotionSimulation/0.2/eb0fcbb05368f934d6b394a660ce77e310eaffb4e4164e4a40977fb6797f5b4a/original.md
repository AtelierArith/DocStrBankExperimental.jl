```
squared_transfer!(Hf2::Vector{T}, f::Vector{T}, sdof::Oscillator) where T<:Real
```

Computes the square of the modulus of the transfer function of a SDOF for a vector of frequencies in place: 	- `Hf2::Vector` is the pre-allocated vector into which the results are stored     - `f::Vector` is the vector of frequencies     - `sdof::Oscillator` is the oscillator instance Inputs derive from the `Real` type and so are differentiable.

# Examples

```julia-repl
    f = collect(range(0.1, stop=10.0, step=0.01))
    sdof = Oscillator(1.0)
    Hf2 = similar(f)
    squared_transfer!(Hf2, f, sdof)
```
