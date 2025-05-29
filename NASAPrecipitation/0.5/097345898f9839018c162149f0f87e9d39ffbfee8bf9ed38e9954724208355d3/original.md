```
getLandSea(
    npd :: NASAPrecipitationDataset,
    geo :: GeoRegion = GeoRegion("GLB");
    returnlsd = true,
    FT = Float32
) -> LandSea
```

Retrieve the Land-Sea Mask data for the `NASAPrecipitationDataset` specified.

# Arguments

  * `npd` : The `NASAPrecipitationDataset` specified, can be either IMERG or TRMM, the function will download the relevant Land-Sea mask without needing further specification.
  * `geo` : The GeoRegion of interest

# Keyword Arguments

  * `returnlsd` : If `true` return the data as a `LandSea` dataset. Otherwise, the data is simply saved into the npd.maskpath directory.
