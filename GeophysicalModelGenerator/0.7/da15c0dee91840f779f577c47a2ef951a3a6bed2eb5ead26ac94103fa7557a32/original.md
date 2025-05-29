```
Lon, Lat, Depth = lonlatdepth_grid(Lon::Any, Lat::Any, Depth:Any)
```

Creates 3D arrays of `Lon`, `Lat`, `Depth` from 1D vectors or numbers

# Example 1: Create 3D grid

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10:20,30:40,(-10:-1)km);
julia> size(Lon)
(11, 11, 10)
```

# Example 2: Create 2D lon/lat grid @ a given depth

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10:20,30:40,-50km);
julia> size(Lon)
(11, 11)
```

# Example 3: Create 2D lon/depth grid @ a given lat

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10:20,30,(-10:-1)km);
julia> size(Lon)
(11, 11)
```

# Example 4: Create 1D vertical line @ a given lon/lat point

```julia-repl
julia> Lon,Lat,Depth =  lonlatdepth_grid(10,30,(-10:-1)km);
julia> size(Lon)
(10, )
```
