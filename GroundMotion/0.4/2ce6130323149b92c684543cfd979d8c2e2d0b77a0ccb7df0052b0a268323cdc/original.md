Mutable type for output INTENSITY data from GMPE modeling functions. The INTENSITY is Seismic Scale according to Russian GOSTR 57546-2017. It can be easily converted from PGA, see `convert_from_pga_to_ssi` functiuon.

Fields:

```
  lon   :: Float64 
  lat   :: Float64 
  ssi   :: Float64 
```

Latitude and longitude assumes degrees for WGS84 ellipsoid. `ssi` is intensity measure from 1.00 to 12.00.
