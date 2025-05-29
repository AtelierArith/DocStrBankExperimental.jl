```
votemap(DataSets::Vector{GeoData}, criteria::Vector{String}, dims=(50,50,50))
```

Creates a Vote map which shows consistent features in different 2D/3D tomographic datasets.

The way it works is:

  * Find a common region between the different GeoData sets (overlapping lon/lat/depth regions)
  * Interpolate the fields of all DataSets to common coordinates
  * Filter data points in one model (e.g., areas with a velocity anomaly > 2 percent). Set everything that satisfies this criteria to 1 and everything else to 0.
  * Sum the results of the different datasets

If a feature is consistent between different datasets, it will have larger values.

# Example

We assume that we have 2 seismic velocity datasets `Data_Zhao_Pwave` and `DataKoulakov_Alps`:

```julia
julia> Data_Zhao_Pwave
GeoData
  size  : (121, 94, 101)
  lon   ϵ [ 0.0 : 18.0]
  lat   ϵ [ 38.0 : 51.95]
  depth ϵ [ -1001.0 km : -1.0 km]
  fields: (:dVp_Percentage,)
julia> DataKoulakov_Alps
  GeoData
    size  : (108, 81, 35)
    lon   ϵ [ 4.0 : 20.049999999999997]
    lat   ϵ [ 37.035928143712574 : 49.01197604790419]
    depth ϵ [ -700.0 km : -10.0 km]
    fields: (:dVp_percentage, :dVs_percentage)
```

You can create a votemap which combines the two data sets with:

```julia
julia> Data_VoteMap = votemap([Data_Zhao_Pwave,DataKoulakov_Alps],["dVp_Percentage>2.5","dVp_percentage>3.0"])
GeoData
  size  : (50, 50, 50)
  lon   ϵ [ 4.0 : 18.0]
  lat   ϵ [ 38.0 : 49.01197604790419]
  depth ϵ [ -700.0 km : -10.0 km]
  fields: (:votemap,)
```

You can also create a votemap of a single dataset:

```julia
julia> Data_VoteMap = votemap(Data_Zhao_Pwave,"dVp_Percentage>2.5", dims=(50,51,52))
GeoData
  size  : (50, 51, 52)
  lon   ϵ [ 0.0 : 18.0]
  lat   ϵ [ 38.0 : 51.95]
  depth ϵ [ -1001.0 km : -1.0 km]
  fields: (:votemap,)
```
