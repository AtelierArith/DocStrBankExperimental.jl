```
CTMRGEnv(
    [f=randn, T=ComplexF64], D_north::P, D_east::P, chi_north::S, [chi_east::S], [chi_south::S], [chi_west::S];
    unitcell::Tuple{Int,Int}=(1, 1),
) where {P<:ProductSpaceLike,S<:ElementarySpaceLike}
```

Construct a CTMRG environment by specifying the north and east virtual spaces of the corresponding [`InfiniteSquareNetwork`](@ref) and the north, east, south and west virtual spaces of the environment. The network unit cell can be specified by the `unitcell` keyword argument. By default, the virtual environment spaces for all directions are taken to be the same.

The environment virtual spaces for each site correspond to virtual space of the corresponding edge tensor for each direction.
