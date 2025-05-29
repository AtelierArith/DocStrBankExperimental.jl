```
bathymetry(contour::Int = 2000)
```

Convenient acccess to ocean bathymetry datasets. Currently tested on: https://www.naturalearthdata.com/downloads/10m-physical-vectors/10m-bathymetry/

The function returns a MultiPolygon describing the bathymetry at a given depth contour. The following depths should be available: `[10000, 9000, 8000, 7000, 6000, 5000, 4000, 3000, 2000, 1000, 200, 0]`
