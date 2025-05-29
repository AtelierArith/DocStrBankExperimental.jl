```
spread(points::Matrix{<:Real}, initial::Matrix{<:Real}, friction::Matrix{<:Real}; res=1, limit=Inf)
```

Total friction distance spread from `points` as by *Tomlin (1983)* [^tomlin1983]. This is also the method implemented by [PCRaster](https://pcraster.geo.uu.nl/pcraster/4.0.2/doc/manual/op_spread.html).

# Output

  * `Array{Float64,2}` Total friction distance

# Arguments

  * `points::Matrix{<:Real}` Input Array
  * `initial::Matrix{<:Real}` Factor to exaggerate elevation
  * `friction::Matrix{<:Real}` Resolution of cell size
  * `res=1` Resolution or cell size
  * `limit=Inf` Initial fill value

[^tomlin1983]: Tomlin, Charles Dana. 1983. Digital Cartographic Modeling Techniques in Environmental Planning. Yale University.
