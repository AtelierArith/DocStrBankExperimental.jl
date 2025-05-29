```
CTMRGEnv(
    [f=randn, T=ComplexF64], Ds_north::A, Ds_east::A, chis_north::B, [chis_east::B], [chis_south::B], [chis_west::B]
) where {A<:AbstractMatrix{<:SpaceLike}, B<:AbstractMatrix{<:ElementarySpaceLike}}
```

Construct a CTMRG environment by specifying matrices of north and east virtual spaces of the corresponding partition function and the north, east, south and west virtual spaces of the environment. Each respective matrix entry corresponds to a site in the unit cell. By default, the virtual environment spaces for all directions are taken to be the same.

The environment virtual spaces for each site correspond to the north or east virtual space of the corresponding edge tensor for each direction. Specifically, for a given site `(r, c)`, `chis_north[r, c]` corresponds to the east space of the north edge tensor, `chis_east[r, c]` corresponds to the north space of the east edge tensor, `chis_south[r, c]` corresponds to the east space of the south edge tensor, and `chis_west[r, c]` corresponds to the north space of the west edge tensor.

Each entry of the `Ds_north` and `Ds_east` matrices corresponds to an effective local space of the partition function, represented as a tuple of elementary spaces encoding a product space. This can either contain a single elementary space for the case of a partition function defined in terms of local rank-4 tensors, or a tuple of elementary spaces representing a product space for the case of a partition function representing overlaps of PEPSs and PEPOs.
