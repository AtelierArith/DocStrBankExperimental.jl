```
get_growingseason(GPPd, tGPP; ws=15, min_int=5, warngap=true)
```

Filters annual time series for growing season based on smoothed daily GPP data.

# Arguments

  * `GPPd`:    daily GPP (any unit)
  * `tGPP`:    GPP threshold (fraction of 95th percentile of the GPP time series).              Takes values between 0 and 1.

optional               

  * `ws`:      window size used for GPP time series smoothing
  * `min_int`: minimum time interval in days for a given state of growing season
  * `warngap`: set to false to suppress warning on too few non-missing data

# Details

The basic idea behind the growing season filter is that vegetation is  considered to be active when its carbon uptake (GPP) is above a specified  threshold, which is defined relative to the peak GPP (95th percentile)  observed in the year.  The GPP-threshold is calculated as:

$GPP_{threshold} = quantile(GPPd,0.95)*tGPP$

GPPd time series are smoothed with a moving average to avoid fluctuations  in the delineation of the growing season. The window size defaults to 15  days, but depending on the ecosystem, other values can be appropriate. 

The argument `min_int` serves to avoid short fluctuations in the  status growing season vs. no growing season by defining a minimum length of the status. If a time interval shorter than `min_int` is labeled as growing season or non-growing season, it is changed to the status of  the neighboring values, i.e its opposite.

# Value

A NamedTuple with entries

  * `is_growingseason`: a `BitVector` of the same length as the input GPPd in which `false`  indicate no growing season (dormant season) and `true` indicate growing season.
  * `GPPd_smoothed`: smoothed GPPd
