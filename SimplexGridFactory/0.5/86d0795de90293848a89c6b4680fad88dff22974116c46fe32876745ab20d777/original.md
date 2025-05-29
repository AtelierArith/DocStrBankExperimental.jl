```
function simplexgrid(Generator;
                     points=Array{Cdouble,2}(undef,0,0),
                     bfaces=Array{Cint,2}(undef,0,0),
                     bfaceregions=Array{Cint,1}(undef,0),
                     regionpoints=Array{Cdouble,2}(undef,0,0),
                     regionnumbers=Array{Cint,1}(undef,0),
                     regionvolumes=Array{Cdouble,1}(undef,0);
                     kwargs...
                  )
```

Create Grid from a number of input arrays. The 2D input arrays are transposed if necessary and converted to the proper data types for Triangulate or TetGen

This conversion is not performed if the data types are those indicated in the defaults and the leading dimension of 2D arrays corresponds to the space dimension.

See [`default_options`](@ref) for available `kwargs`.
