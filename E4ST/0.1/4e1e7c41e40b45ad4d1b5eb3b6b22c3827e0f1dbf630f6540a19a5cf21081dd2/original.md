```
get_cf_max(data, gen_idx, year_idx, hour_idx)
```

Returns max capacity factor at a given time.  It is based on the lower of gen properties `af` (availability factor) and optional `cf_max` (capacity factor).  If it is below `config[:cf_threshold]`, it is rounded to zero.
