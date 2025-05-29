```
get_datetime_for_doy_hour(doy, hour=12; year = 2030)
```

Create DateTime for given day*of*year and hour. Hour defaults to noon and year to 2030, a near future where earth axis  precession does not differ too much from year where the function  is called. Fractional hours can be provided.

# Examples

```jldoctest output = false
get_datetime_for_doy_hour(2; year = 2021)
# output
2021-01-02T12:00:00
```
