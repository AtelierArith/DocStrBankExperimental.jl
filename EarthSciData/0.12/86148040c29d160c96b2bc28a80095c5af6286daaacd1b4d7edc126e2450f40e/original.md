```julia
GEOSFP(domain, domaininfo; name, stream)

```

A data loader for GEOS-FP data as archived for use with GEOS-Chem classic.

Domain options (as of 2022-01-30):

  * 4x5
  * 0.125x0.15625_AS
  * 0.125x0.15625_EU
  * 0.125x0.15625_NA
  * 0.25x0.3125
  * 0.25x0.3125_AF
  * 0.25x0.3125_AS
  * 0.25x0.3125_CH
  * 0.25x0.3125_EU
  * 0.25x0.3125_ME
  * 0.25x0.3125_NA
  * 0.25x0.3125_OC
  * 0.25x0.3125_RU
  * 0.25x0.3125_SA
  * 0.5x0.625
  * 0.5x0.625_AS
  * 0.5x0.625_CH
  * 0.5x0.625_EU
  * 0.5x0.625_NA
  * 2x2.5
  * 4x5
  * C180
  * C720
  * NATIVE
  * c720

The native data type for this dataset is Float32.

`stream` specifies whether the data should be streamed in as needed or loaded all at once.

See http://geoschemdata.wustl.edu/ExtData/ for current data domain options.
