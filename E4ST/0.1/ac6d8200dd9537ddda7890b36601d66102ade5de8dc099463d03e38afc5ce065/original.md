```
modify_setup_data!(ret::Retrofit, config, data)
```

  * Calls [`init!(ret::Retrofit, config, data)`](@ref) to initialize the data.
  * Makes a `Dict` in `data[:retrofits]` to keep track of the retrofits being produced for each retrofit.
  * Loops through the rows of the `gen` table

      * Checks to see if the can be retrofitted via [`can_retrofit(ret::Retrofit, row)`](@ref)
      * Constructs the new retrofitted generator via [`retrofit!(ret::Retrofit, row)`](@ref)
      * Constructs one new one for each year in the simulation.
