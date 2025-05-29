```
spInterp(weights::AbstractMatrix, data::AbstractMatrix; progress=true)
```

```julia
sites = [st.lon st.lat]
alt = st[:, :alt]
data = repeat(alt, 1, 24)' |> collect

b = bbox(70, 15, 140, 55)
lon, lat = bbox2dims(b; cellsize=0.5)
nlon, nlat = length(lon), length(lat)
ra = rast(rand(nlon, nlat), b)

weights = weights_adw(ra, sites)
@time zs = spInterp(weights, data)
```
