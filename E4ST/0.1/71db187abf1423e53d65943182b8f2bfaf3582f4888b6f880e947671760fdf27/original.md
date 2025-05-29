```
retrofit!(ret::Retrofit, newgen) -> ::AbstractDict
```

This function should change `newgen` to have the properties of the retrofit.  `newgen` is a `Dict` containing all the properties of the original generator, but with the the following fields already changed:

  * `year_retrofit` - set to the year to be retrofitted
  * `retrofit_original_gen_idx` - set to the index of the gen table for the original generator
  * `capex` - set to 0 to avoid double-paying capex for the already-built generator.  Capex added to `newgen` should only be the capital costs for the retrofit itself.  E4ST should already be accounting capex in `past_capex` for the original generator.
  * `pcap0` - set to 0
  * `transmission_capex` - set to 0
  * `build_status` - set to `unretrofitted`
