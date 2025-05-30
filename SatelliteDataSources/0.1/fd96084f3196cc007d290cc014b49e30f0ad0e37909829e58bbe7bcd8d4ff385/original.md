Implements the `AbstractSatellite` interface for Sentinel 2.

The user must specify a resolution of 10, 20, or 60 meters.

**Supported Bands (10m):** `:B02`, `:B03`, `:B04`, `:B08`

**Supported Bands (20m):** `:B02`, `:B03`, `:B04`, `:B05`, `:B06`, `:B07`, `:B8A`, `:B11`, `:B12`

**Supported Bands (60m):** `:B01`, `:B02`, `:B03`, `:B04`, `:B05`, `:B06`, `:B07`, `:B8A`, `:B09`, `:B11`, `:B12`

**Supported Colors (10m):** `:blue`, `:green`, `:red`, `:nir`  

**Supported Colors (20m and 60m):** `:blue`, `:green`, `:red`, `:nir`, `:swir1`, `:swir2`  

**Supported Masks (20m and 60m):** `:cloud_shadow`, `:clouds_med`, `:clouds_high`, `:cirrus`, `:vegetation`, `:soil`, `:water`, `:snow`  
