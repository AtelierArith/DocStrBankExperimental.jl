```
set_adduct_name!(nm::AbstractString, adduct::AbstractAdduct)
```

Set `nm` to be `adduct` for parsing specific adduct string by `ADDUCTS[:NAME]`.

For custumized adduct type, this function is required to make `nm` parsed into `adduct` by `parse_adduct`. 
