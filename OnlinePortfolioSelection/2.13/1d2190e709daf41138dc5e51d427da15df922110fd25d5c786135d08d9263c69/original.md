```
PAMR2{T<:AbstractFloat}<: PAMRModel
```

Create a PAMR2 object. Also, see [`PAMR`](@ref), and [`PAMR1`](@ref).

# Keyword Arguments

  * `C::AbstractFloat=1.`: Aggressiveness parameter.

# Example

```julia
model = PAMR2(C=0.02)
```
