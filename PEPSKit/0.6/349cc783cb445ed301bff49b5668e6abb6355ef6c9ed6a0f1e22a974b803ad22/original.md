```
CTMRGEnv(
    [f=randn, T=ComplexF64], network::InfiniteSquareNetwork, chis_north::A, [chis_east::A], [chis_south::A], [chis_west::A]
) where {A<:AbstractMatrix{<:ElementarySpaceLike}}}
```

Construct a CTMRG environment by specifying a corresponding [`InfiniteSquareNetwork`](@ref), and the north, east, south and west virtual spaces of the environment as matrices. Each respective matrix entry corresponds to a site in the unit cell. By default, the virtual spaces for all directions are taken to be the same.

The environment virtual spaces for each site correspond to the north or east virtual space of the corresponding edge tensor for each direction. Specifically, for a given site `(r, c)`, `chis_north[r, c]` corresponds to the east space of the north edge tensor, `chis_east[r, c]` corresponds to the north space of the east edge tensor, `chis_south[r, c]` corresponds to the east space of the south edge tensor, and `chis_west[r, c]` corresponds to the north space of the west edge tensor.
