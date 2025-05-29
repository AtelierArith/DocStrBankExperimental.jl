```
subcube(cube::String; bands=Int[], bandnames=String[], layers=Int[])
```

Extracts a subcube from `cube` with the layers in the `bands` vector, case in which we will search for bands named "Band band[k]", or those whose names correspond (even partially and case insensitive) to the descriptions in `bandnames` string vector. This means that the options `bands` and `bandnames` can only be used in 'cubes' with bands description. The `layers` option blindly extract the `cube` planes listed in the `layer` vector.

Returns a GMTimage

```
subcube(cube::Union{GMT.GMTimage{UInt16, 3}, AbstractArray{<:AbstractFloat, 3}}; bands=Int[], bandnames=String[], layers=Int[])
```

Does the same but from an already in memory cube. Returns a type equal to the input type. No views, a data copy.

### Example

Extracts the Red, Green and Blue layers from a Landsat 8 cube created with `cutcube`

```
Irgb = subcube("LC08__cube.tiff", bandnames = ["red", "green", "blue"])
```
