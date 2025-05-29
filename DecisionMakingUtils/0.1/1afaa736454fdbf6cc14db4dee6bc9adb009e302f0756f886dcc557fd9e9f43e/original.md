```
LinearNormalization{T}(a::T,b::T)
```

This is a functor that normalizes a vector x as $(x - a) * b$. This is the standard interface for all  linear normalizations such as mapping to $[0,1]$, $[-1,1]$ and mean zero standard deviation one.  LinearNormalization also supports the functions Base.lenght and Base.eltype.

See also: [`PosNegNormalization`](@ref), [`GaussianNormalization`](@ref)

# Examples

```jldoctest
julia> nrm = LinearNormalization([0.1, 2.0], [1.0, 0.5]);

julia> x = [1.0, 2.0];

julia> nrm(x)
2-element Vector{Float64}:
 0.9
 0.0

julia> nrm = LinearNormalization(2);  # no scaling to input vector

julia> nrm(x)
2-element Vector{Float64}:
 1.0
 2.0

julia> low = [0.0, -1.0];

julia> high = [3.0, 0.5];

julia> nrm = ZeroOneNormalization(low, high);  # normalize each entry to [0,1]

julia> x = [1.0, 0.0];

julia> feats = nrm(x)
2-element Array{Float64,1}:
0.3333333333333333
0.6666666666666666

julia> y = zero(x);  # create buffer to prevent allocations

julia> feats = nrm(y, x);  # no allocation return

julia> nrm = PosNegNormalization(low, high);  # normalize each entry to [0,1]

julia> nrm(x)
2-element Vector{Float64}:
 -0.3333333333333333
  0.3333333333333333

julia> μ = [0.0, 1.0];  # vector of means

julia> σ = [1.0, 2.0];  # vector of standard deviations

julia> nrm = GaussianNormalization(μ, σ);  # normalize x to be mean 0 and standard deviation 1

julia> nrm(x)
2-element Vector{Float64}:
  1.0
 -0.5
```
