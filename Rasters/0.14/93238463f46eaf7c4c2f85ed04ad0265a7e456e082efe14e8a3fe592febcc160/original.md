```
cellarea([method], x)
```

Gives the approximate area of each gridcell of `x`. By assuming the earth is a sphere, it approximates the true size to about 0.1%, depending on latitude. 

Run `using ArchGDAL` or `using Proj` to make this method fully available.

  * `method`: You can specify whether you want to compute the area in the plane of your projection `Planar()` or on a sphere of some radius `Spherical(; radius=...)`(the default).
  * `Spherical` will compute cell area on the sphere, by transforming all points back to long-lat.  You can specify the radius by the `radius` keyword argument here.  By default, this is `6371008.8`, the mean radius of the Earth.
  * `Planar` will compute cell area in the plane of the CRS you have chosen.  Be warned that this will likely be incorrect for non-equal-area projections.

Returns a Raster with the same x and y dimensions as the input,  where each value in the raster encodes the area of the cell (in meters by default).

## Example

```julia
using Rasters, Proj, Rasters.Lookups
xdim = X(Projected(90.0:10.0:120; sampling=Intervals(Start()), crs=EPSG(4326)))
ydim = Y(Projected(0.0:10.0:50; sampling=Intervals(Start()), crs=EPSG(4326)))
myraster = rand(xdim, ydim)
cs = cellarea(myraster)

# output
╭───────────────────────╮
│ 4×6 Raster{Float64,2} │
├───────────────────────┴─────────────────────────────────────────────────── dims ┐
  ↓ X Projected{Float64} 90.0:10.0:120.0 ForwardOrdered Regular Intervals{Start},
  → Y Projected{Float64} 0.0:10.0:50.0 ForwardOrdered Regular Intervals{Start}
├───────────────────────────────────────────────────────────────────────── raster ┤
  extent: Extent(X = (90.0, 130.0), Y = (0.0, 60.0))

  crs: EPSG:4326
└─────────────────────────────────────────────────────────────────────────────────┘
   ↓ →  0.0        10.0        20.0        30.0            40.0      50.0
  90.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
 100.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
 110.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
 120.0  1.23017e6   1.19279e6   1.11917e6   1.01154e6  873182.0  708290.0
```

WARNING: This feature is experimental. It may change in future versions, and may not be 100% reliable in all cases. Please file github issues if problems occur.
