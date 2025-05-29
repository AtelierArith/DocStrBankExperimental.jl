```julia
struct Renormalize{T} <: VLBISkyModels.ModelModifier{T}
```

Renormalizes the flux of the model to the new value `scale*flux(model)`. We have also overloaded the Base.:* operator as syntactic sugar although I may get rid of this.

# Example

```julia-repl
julia> modify(Gaussian(), Renormalize(2.0)) == 2.0*Gaussian()
true
```
