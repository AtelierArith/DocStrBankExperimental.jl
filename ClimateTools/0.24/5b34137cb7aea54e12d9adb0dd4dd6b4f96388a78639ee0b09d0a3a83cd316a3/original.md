```
ClimGrid{A <: AxisArray}
```

In-memory representation of Climate Forecast netCDF files. struct ClimGrid

data::AxisArray # Data

longrid::AbstractArray{N,2} where N # the longitude grid

latgrid::AbstractArray{N,2} where N # the latitude grid

msk::Array{N, 2} where N # Data mask (NaNs and 1.0)

grid_mapping::Dict#{String, Any} # bindings for native grid

dimension_dict::Dict

model::String

frequency::String # Day, month, years

experiment::String # Historical, RCP4.5, RCP8.5, etc.

run::String

project::String # CORDEX, CMIP5, etc.

institute::String # UQAM, DMI, etc.

filename::String # Path of the original file

dataunits::String # Celsius, kelvin, etc.

latunits::String # latitude coordinate unit

lonunits::String # longitude coordinate unit

variable::String # Type of variable (i.e. can be the same as "typeofvar", but it is changed when calculating indices)

typeofvar::String # Variable type (e.g. tasmax, tasmin, pr)

typeofcal::String # Calendar type

timeattrib::Dict # Time attributes (e.g. days since ... )

varattribs::Dict # Variable attributes dictionary

globalattribs::Dict # Global attributes dictionary

end
