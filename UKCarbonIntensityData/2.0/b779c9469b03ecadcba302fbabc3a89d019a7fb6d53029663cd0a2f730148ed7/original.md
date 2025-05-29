```
get_todays_forecast(;regional::Bool=false, region::AbstractString="")
```

Returns a DataFrame of the forecast and actual carbon intensity between for the 48 hours of the day the query is called. By default return national level data, pass `regional=true` to return data with regional spatial resolution. To retreive data for a single region, pass the `region = <desired region>` where <desired region> must be included in the the `AVAILABLE_REGIONS`.
