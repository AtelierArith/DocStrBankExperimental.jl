```
load_GMG(filename::String, dir=pwd(); maxattempts=5)
```

Loads a `GeoData`/`CartData`/`UTMData` data set from jld2 file `filename` Note: the `filename` can also be a remote `url`, in which case we first download that file to a temporary directory before opening it. We make `maxattempts` attempts to download it before giving up.

# Example 1 - Load local file

```julia
julia> data = load_GMG("test")
GeoData 
  size      : (4, 3, 3)
  lon       ϵ [ 1.0 : 10.0]
  lat       ϵ [ 11.0 : 19.0]
  depth     ϵ [ -20.0 : -10.0]
  fields    : (:DataFieldName,)
  attributes: ["note"]
```

# Example 2 - remote download

```julia
julia> url  = "https://seafile.rlp.net/f/10f867e410bb4d95b3fe/?dl=1"
julia> load_GMG(url)
GeoData 
  size      : (149, 242, 1)
  lon       ϵ [ -24.875 : 35.375]
  lat       ϵ [ 34.375 : 71.375]
  depth     ϵ [ -11.76 : -34.7]
  fields    : (:MohoDepth,)
  attributes: ["author", "year"]
```
