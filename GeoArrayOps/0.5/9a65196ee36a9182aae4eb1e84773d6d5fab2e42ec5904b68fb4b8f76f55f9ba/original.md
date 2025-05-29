```
spread2(points::Matrix{<:Real}, initial::Matrix{<:Real}, friction::Matrix{<:Real}; res=1, limit=Inf, iterations=3)
```

Pushbroom method for friction costs as discussed by *Eastman (1989) [^eastman1989]. This method should scale much better (linearly) than the [^tomlin1983] method, but can require more `iterations` than set by default (3) in the case of maze-like, uncrossable obstacles.

# Output

  * `Array{Float64,2}` Total friction distance

# Arguments

  * `points::Matrix{<:Real}` Input Array
  * `initial::Matrix{<:Real}` Factor to exaggerate elevation
  * `friction::Matrix{<:Real}` Resolution of cell size
  * `res=1` Resolution or cell size
  * `limit=Inf` Initial fill value
  * `iterations=3` Number of pushbroom iterations

[^eastman1989]: Eastman, J. Ronald. 1989. ‘Pushbroom Algorithms for Calculating Distances in Raster Grids’. In Proceedings, Autocarto, 9:288–97.
