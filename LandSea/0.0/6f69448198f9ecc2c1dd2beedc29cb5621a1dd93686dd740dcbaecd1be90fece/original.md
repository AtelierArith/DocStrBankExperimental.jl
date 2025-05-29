```
LandSeaData
```

Abstract supertype for LandSea Datasets. All `LandSeaData` types contain the following fields:

  * `lon` - Vector containing the longitude points for the Land-Sea Dataset
  * `lat` - Vector containing the latitude points for the Land-Sea Dataset
  * `lsm` - Array containing data regarding the Land-Sea Mask. 1 is Land, 0 is Ocean, NaN is outside the bounds of the GeoRegion
