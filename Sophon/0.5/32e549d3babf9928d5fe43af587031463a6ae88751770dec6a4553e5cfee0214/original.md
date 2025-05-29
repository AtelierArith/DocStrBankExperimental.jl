```
FourierFeature(in_dims::Int, std::NTuple{N,Pair{S,T}}) where {N,S,T<:Int}
FourierFeature(in_dims::Int, frequencies::NTuple{N, T}) where {N, T <: Real}
FourierFeature(in_dims::Int, out_dims::Int, std::Real)
```

Fourier Feature Network.

# Arguments

  * `in_dims`: Number of the input dimensions.
  * `std`: A tuple of pairs of `sigma => out_dims`, where `sigma` is the standard deviation of the Gaussian distribution.

$$
\phi^{(i)}(x)=\left[\sin \left(2 \pi W^{(i)} x\right) ; \cos 2 \pi W^{(i)} x\right],\ W^{(i)} \sim \mathcal{N}\left(0, \sigma^{(i)}\right),\ i\in 1, \dots, D
$$

  * `frequencies`: A tuple of frequencies $(f1,f2,...,fn)$.

$$
\phi^{(i)}(x)=\left[\sin \left(2 \pi f_i x\right) ; \cos 2 \pi f_i x\right]
$$

# Parameters

If `std` is used, then parameters are `W`s in the formula.

# Inputs

  * `x`: `AbstractArray` with `size(x, 1) == in_dims`.

# Returns

  * $[\phi^{(1)}, \phi^{(2)}, ... ,\phi^{(D)}]$ with `size(y, 1) == sum(last(modes) * 2)`.

# Examples

```julia
julia> f = FourierFeature(2,10,1) # Random Fourier Feature
FourierFeature(2 => 10)

julia> f = FourierFeature(2, (1 => 3, 50 => 4)) # Multi-scale Random Fourier Features
FourierFeature(2 => 14)

julia>  f = FourierFeature(2, (1,2,3,4)) # Predefined frequencies
FourierFeature(2 => 16)
```

# References

[rahimi2007random](@cite)

[tancik2020fourier](@cite)

[wang2021eigenvector](@cite)
