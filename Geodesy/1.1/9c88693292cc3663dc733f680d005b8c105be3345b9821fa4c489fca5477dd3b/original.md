```
UTM(x, y, z = 0.0)
```

Universal transverse Mercator (UTM) coordinates. Common projection type for world points. Zone not included in coordinates - it is a parameterized in the relavant transformations `UTMfromLLA` and `LLAfromUTM` (see also the `UTMZ` type).

This type may be used to parameterize UPS coordinates (Universal Polar Stereographic) to accurately represent the polar regions, in zone "0".
