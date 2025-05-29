```
getraster(T::Type{CHELSA{Future{BioClimPlus}}}, [layer]; date) => String
```

Download CHELSA [`BioClimPlus`](@ref) data, choosing layers from: `[:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19, :hurs_max, :clt_max, :sfcWind_max, :vpd_max, :rsds_max, :pet_penman_max, :cmi_max, :hurs_min, :clt_min, :sfcWind_min, :vpd_min, :rsds_min, :pet_penman_min, :cmi_min, :hurs_mean, :clt_mean, :sfcWind_mean, :vpd_mean, :rsds_mean, :pet_penman_mean, :cmi_mean, :hurs_range, :clt_range, :sfcWind_range, :vpd_range, :rsds_range, :pet_penman_range, :cmi_range, :gdd0, :gddlgd0, :gdgfgd0, :ngd0, :gdd5, :gddlgd5, :gdgfgd5, :ngd5, :gdd10, :gddlgd10, :gdgfgd10, :ngd10, :fcf, :fgd, :lgd, :scd, :gsl, :gst, :gsp, :npp, :swb, :swe, :kg0, :kg1, :kg2, :kg3, :kg4, :kg5]`.

See the docs for [`Future`](@ref) for model choices.

Without a layer argument, all layers will be downloaded, and a `NamedTuple` of paths  returned.

## Keywords

  * `date`: a `Date` or `DateTime` object, a Vector, or Tuple of start/end dates.   Note that CHELSA CMIP5 only has two datasets, for the periods 2041-2060 and   2061-2080. CMIP6 has datasets for the periods 2011-2040, 2041-2070, and 2071-2100.   Dates must fall within these ranges.

## Example
