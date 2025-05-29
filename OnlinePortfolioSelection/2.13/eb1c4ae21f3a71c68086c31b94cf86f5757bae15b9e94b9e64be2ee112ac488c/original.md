```
PAMR1{T<:AbstractFloat}<: PAMRModel
```

Create a PAMR1 object. Also, see [`PAMR`](@ref), and [`PAMR2`](@ref).

# Keyword Arguments

  * `C::AbstractFloat=1.`: Aggressiveness parameter.

# Example

```julia
model = PAMR1(C=0.02)
```
