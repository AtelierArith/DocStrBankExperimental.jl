```
download(
    e5ds :: Union{ERA5Hourly,ERA5Monthly},
    evar :: Vector{SingleVariable},
    ereg :: ERA5Region;
    overwrite :: Bool = false
) -> nothing
```

Downloads ERA5 data from the CDS datastore for a specified variable and geographic region.  There is no python option for this method.

You must have installed the CDSAPI on your machine and have accepted the terms and conditions on the CDS website in order for this to work.

# Arguments

  * `e5ds` : The ERA5Dataset specified (Hourly or Monthly)

      * `e5ds.start` defines the start date
      * `e5ds.stop` defines the end date
      * `e5ds.path` defines the path to which all reanalysis data is saved
  * `evar` : Specifies a vector of Single-Level variables to be downloaded in a temporary file. Once downloaded, the different variables will be extracted out and saved in their respective folders.
  * `ereg` : Specifies the `GeoRegion` and the resolution of the data to be downloaded
  * `overwrite` : `false` by default. If set to true, existing data will be overwritten.
