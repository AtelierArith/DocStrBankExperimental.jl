```
CTMRGEnv(
    [f=randn, T=ComplexF64,] network::InfiniteSquareNetwork, chi_north::S, [chi_east::S], [chi_south::S], [chi_west::S],
) where {S<:ElementarySpaceLike}
```

Construct a CTMRG environment by specifying a corresponding [`InfiniteSquareNetwork`](@ref), and the north, east, south and west virtual spaces of the environment. By default, the virtual spaces for all directions are taken to be the same.

The environment virtual spaces for each site correspond to virtual space of the corresponding edge tensor for each direction.
