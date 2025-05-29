```
DiffusionEquation(K[; C, sym])
DiffusionEquation{m}(K[; C, sym])
```

Nonlinear diffusion equation.

# Arguments

  * `K`: diffusivity function (if `C` is not given) or conductivity function, defined in terms of the unknown.

# Keyword arguments

  * `C=nothing`: optional capacity function, defined in terms of the unknown.
  * `sym=:u`: symbol used to represent the unknown function in the output.

# Type parameters

  * `m=1`: number of spatial dimensions:

      * 1 for non-radial one-dimensional diffusion (default);
      * 2 for radial diffusion in polar or cylindrical coordinates;
      * 3 for radial diffusion in spherical coordinates.

# Examples

```jldoctest; setup = :(using Fronts)
julia> D(u) = u^4
D (generic function with 1 method)

julia> eq = Fronts.DiffusionEquation(D)
∂u/∂t = ∂(D(u)*∂u/∂r)/∂r

julia> eq = Fronts.DiffusionEquation{2}(D)
∂u/∂t = 1/r*∂(r*D(u)*∂u/∂r)/∂r

julia> eq = Fronts.DiffusionEquation{3}(D, sym=:c)
∂c/∂t = 1/r²*∂(r²*D(c)*∂c/∂r)/∂r
```
