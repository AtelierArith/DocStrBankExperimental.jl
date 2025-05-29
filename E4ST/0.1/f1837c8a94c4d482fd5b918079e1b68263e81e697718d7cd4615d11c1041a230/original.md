```
modify_setup_data!(mod::CCUS, config, data) -> nothing
```

Does the following:

  * Adds a column for carbon captured, `capt_co2`, based on `emis_co2`, and `capt_co2_percent`
  * reduces `emis_co2` by `capt_co2`
  * Splits up carbon capturing generators into 2 separate generators - one for "saline" and one for "eor", and adjusts the eor emissions by `config[eor_leakage_rate]`
  * Add a column for `ccus_type` - either "eor", "saline", or "na"
  * Adds sets of indices to `data[:ccus_gen_sets]::Vector{Vector{Int64}}`
