```
loadTDesign(t::Int64, N::Int64, radius::S=10Unitful.mm, center::Vector{V}=[0.0,0.0,0.0]Unitful.mm, filename::String=joinpath(@__DIR__, "TDesigns.hd5")) where {S,V<:Unitful.Length}
```

*Description:* Returns the t-design array for chosen degree t and number of points N

*Input:*

  * `t` - degree
  * `N` - number of points
  * `radius` - radius of the sphere (default: 10mm)
  * `center` - center of the sphere (default: [0.0,0.0,0.0]mm)
  * `filename` - name of the file containing the t-designs (default loads TDesign.hd5)

*Output:*

  * t-design of type SphericalTDesign in Cartesian coordinates containing t, radius, center and positions (which are located on the unit sphere unless `getindex(tdes,i)` is used)
