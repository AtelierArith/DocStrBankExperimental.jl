```
mutable struct Storage <: Modification

Storage(;name, file, build_file="")
```

Storage is represented over sets of time-weighted sequential representative hours for which the following must hold true, for a given storage device:

  * Net charge over the interval must equal zero.
  * Total charge of the device cannot exceed its maximum charge, or go below zero.
  * Initial charge over an interval can be anywhere between 0 and the maximum charge, and is the same initial charge for each time interval.

# Arguments

  * `name` - the name of the [`Modification`](@ref).
  * `file` - the filename of the storage table, where each row represents a storage device. See also [`summarize_table(::Val{:storage})`](@ref)
  * `build_file` - the filename of the buildable storage table, where each row represents a specification for buildable storage.  See also [`summarize_table(::Val{:build_storage})`](@ref)

# Variables Introduced

  * `pcap_stor[stor_idx, yr_idx]` - The discharge power capacity, in MW, of the storage device.
  * `pcharge_stor[stor_idx, yr_idx, hr_idx]` - The charge power, in MW, for a given hour.
  * `pdischarge_stor[stor_idx, yr_idx, hr_idx]` - The discharged power, in MW, for a given hour.
  * `e0_stor[stor_idx, yr_idx, int_idx]` - The starting charge energy (in MWh) for each interval.

# Constraints Introduced

  * `cons_stor_charge_bal[stor_idx, yr_idx, int_idx]` - the charge balancing equation - net charge in each interval is 0
  * `cons_stor_charge_max[stor_idx, yr_idx, int_idx, _hr_idx]` - constrain the stored energy in each hour of each interval to be less than the maximum (function of `pcap_stor` and the discharge duration column of the storage table).  Note `_hr_idx` is the index within the interval, not the normal `hr_idx`
  * `cons_stor_charge_min[stor_idx, yr_idx, int_idx, _hr_idx]` - constrain the stored energy in each hour of each interval to be greater than zero.  Note `_hr_idx` is the index within the interval, not the normal `hr_idx`
  * `cons_pcap_stor_noadd[stor_idx, yr_idx; years[yr_idx] >= storage.year_on[stor_idx]]` - constrain the capacity to be non-increasing after being built. (only in multi-year simulations)
  * `cons_pcap_stor_prebuild[stor_idx, yr_idx; years[yr_idx] < storage.year_on[stor_idx]]` - fix the capacity to zero before being built. (should only happen in multi-year simulations)
  * `cons_pcap_stor_exog[stor_idx, yr_idx]` - constrain the exogenous, unbuilt capacity to equal pcap0 for the first year >= its build year.

# Objective Terms

  * `capex_obj_stor` - the capital expenditures to build the storage device, only non-zero in the build year.  (function of `pcap_stor` and `capex`, and `year_on`)
  * `fom_stor` - the fixed operation and maintenance costs for the storage device (function of `pcap_stor` and `fom` from the storage table)
  * `vom_stor` - the variable operation and maintenance costs for the storage device (function of `pdischarge_stor`, the `vom` column of the storage table, and the hour weights [`get_hour_weights`](@ref))

# Power Balancing Equation

Each storage device can either be on the "gen" side or the "load" side, as specified by the `side` column.

  * "gen" side:

      * `pcharge_stor` gets subtracted from `pgen_bus`
      * `pdischarge_stor` gets added to `pgen_bus`
  * "load" side:

      * `pcharge_stor` gets added to `plserv_bus`
      * `pdischarge_stor` gets subtracted from `plserv_bus`
