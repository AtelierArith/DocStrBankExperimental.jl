```
FourierBasisBuffer(ϕ::FourierBasis)
```

Creates preallocated buffers for a fourier basis to use to avoid making allocations on every call of the basis. 

See also: [`FourierBasis`](@ref)

# Examples

```jldoctest julia> f = FourierBasis(2, 1, 2);

julia> buff = FourierBasisBuffer(f);

julia> x = [0.0, 0.5];

julia> feats = f(buff, x) 6-element Array{Float64,1}:   1.0   6.123233995736766e-17   1.0   6.123233995736766e-17   1.0  -1.0
