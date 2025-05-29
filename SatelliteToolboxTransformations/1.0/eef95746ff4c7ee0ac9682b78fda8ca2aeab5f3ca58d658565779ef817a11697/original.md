```
read_iers_eop(filename::String[, data_type]) -> EopIau1980 | EopIau2000A
```

Read IERS EOP data from the file `filename`. The user must specify if the data is related to the model IAU 1980 (`data_type = Val(:IAU1980)`), which is the default, or to the model IAU 2000A (`data_type = Val(:IAU2000A)`).

!!! note
    The input file **must be exactly the same** as provided by IERS in CSV format. One can download it using the following commands:

      * IAU 1980

        curl -O https://datacenter.iers.org/data/csv/finals.all.csv   wget https://datacenter.iers.org/data/csv/finals.all.csv
      * IAU 2000A

        curl -O https://datacenter.iers.org/data/csv/finals2000A.all.csv   wget https://datacenter.iers.org/data/csv/finals2000A.all.csv


# Returns

  * [`EopIau1980`](@ref) or [`EopIau2000A`](@ref), depending on `data_type`: An object with   the interpolations of the EOP. Notice that the interpolation indexing is set to the   Julian Day.
