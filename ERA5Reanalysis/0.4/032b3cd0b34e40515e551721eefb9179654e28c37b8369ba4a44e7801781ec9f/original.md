```
download(
    e5ds :: Union{ERA5Hourly,ERA5Monthly},
    evar :: PressureVariable,
    ereg :: ERA5Region;
    ispy :: Bool = false,
    pall :: Bool = false,
    ptop :: Int = 0,
    pbot :: Int = 0,
    pvec :: Vector{Int} = [0],
    overwrite :: Bool = false
) -> nothing
```

Downloads ERA5 data from the CDS datastore for a specified Pressure-Level variable and geographic region.  You can choose to specify (1) one pressure level, (2) a vector of pressure levels or (3) a set of pressure levels defined by their top and bottom levels.  A python option is also available, but this will generate python scripts for all pressure levels.

You must have installed the CDSAPI on your machine and have accepted the terms and conditions on the CDS website in order for this to work.

# Arguments

  * `e5ds` : The ERA5Dataset specified (Hourly or Monthly)

      * `e5ds.start` defines the start date
      * `e5ds.stop` defines the end date
      * `e5ds.path` defines the path to which all reanalysis data is saved
  * `evar` : Specifies a Pressure-Level variable to be downloaded. By default (if `pall` is not selected), then the pressure level closest to what is specified in evar.hPa will be downloaded.
  * `ereg` : Specifies the `GeoRegion` and the resolution of the data to be downloaded
  * `ipsy` : Specifies whether to generate a python script that can be used to download the data instead of Julia. If `true`, scripts for **all** pressure levels will be generated
  * `pall` : Indicates that we are selecting a range of pressure levels to be downloaded at the same time.

      * `ptop` : Indicates the pressure level at the top layer. `ptop` must be < `pbot`
      * `pbot` : Indicates the pressure level at the bottom layer. `pbot` must be > `ptop`
      * `pvec` : Defines a set of pressure levels to download. Overrides `ptop` and `pbot`
  * `overwrite` : `false` by default. If set to true, existing data will be overwritten.
