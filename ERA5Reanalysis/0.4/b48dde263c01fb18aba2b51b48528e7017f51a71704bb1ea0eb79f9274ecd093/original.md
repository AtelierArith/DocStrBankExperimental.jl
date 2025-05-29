```
getLandSea(
    e5ds :: ERA5Dataset,
    ereg :: ERA5Region = ERA5Region("GLB");
    save :: Bool = true,
    returnlsd :: Bool = true,
    smooth    :: Bool = false,
    σlon :: Int = 0,
    σlat :: Int = 0,
    iterations :: Int = 100,
    FT = Float64
) -> LandSea
```

Retrieve the Land-Sea Mask data for the `ERA5Dataset` specified.

# Arguments

  * `e5ds` : The `ERA5Dataset` specified, which downloads the LandSea data into the path specified in `e5ds`.
  * `ereg` : The ERA5Region of interest, each LandSea dataset is different depending on the resolution specified

# Keyword Arguments

  * `save` : If `true`, save a copy of the LandSea dataset in a NetCDF file specified by e5ds.emask for ease of future retrieval (i.e., no need to repeat the download)
  * `returnlsd` : If `true` return the data as a `LandSea` dataset. Otherwise, the data is simply saved into the e5ds.emask directory.
  * `smooth` : If `smooth` = true, then you can smooth the land-sea mask using the Gaussian Filter of ImageFiltering.jl such that the coastline (i.e. the separation between land and ocean) becomes blurred.
  * `σlon` : Smooth in the longitude direction (every increase of 1 in σlon roughly - corresponds to 8 pixels)
  * `σlat` : Smooth in the latitude direction (every increase of 1 in σlat roughly corresponds to 8 pixels)
  * `iterations` : Iterations of gausssian smoothing, the higher, the closer the smoothing follows a semi-log. 50-100 iterations is generally enough.
