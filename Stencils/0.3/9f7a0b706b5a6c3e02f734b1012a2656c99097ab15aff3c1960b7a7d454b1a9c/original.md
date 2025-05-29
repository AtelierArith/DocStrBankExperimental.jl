```
NamedStencil <: AbstractStencil

NamedStencil(; kw...)
NamedStencil(values::NamedTuple)
NamedStencil{Keys}(values)
```

A named stencil that can take arbitrary shapes where each offset position is named. This can make stencil code easier to read by  removing magic numbers.

## Example

```jldoctest
julia> using Stencils

julia> ns = NamedStencil(; west=(0, -1), north=(1, 0), south=(-1, 0), east=(0, 1)) 
NamedStencil{(:west, :north, :south, :east), ((0, -1), (1, 0), (-1, 0), (0, 1)), 1, 2, 4, Nothing}
▄▀▄
 ▀ 

julia> A = StencilArray((1:10) * (1:10)', ns);

julia> stencil(A, (5, 5)).east # we can access values by name
30

julia> mapstencil(s -> s.east + s.west, A); # and use them in `mapstencil` functions
```

We can also take some shortcuts, and just name an existing stencil:

```julia
julia> ns = NamedStencil{(:w,:n,:s,:e)}(VonNeumann(1)) 
```

The stencil radius is calculated from the most distant coordinate, and the dimensionality `N` of the stencil is taken from the length of the first coordinate, e.g. `1`, `2` or `3`.
