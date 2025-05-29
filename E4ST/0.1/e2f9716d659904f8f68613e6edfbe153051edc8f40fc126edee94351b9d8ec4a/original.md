```
struct AnnualCapacityFactorLimit <: Modification

AnnualCapacityFactorLimit(;name, file)
```

Sets annual capacity factor limits for generators.  Annual capacity factor is defined as the total energy generated in a year divided by the total amount of energy capacity (power capacity times the number of hours in a year).

  * `modify_raw_data!` - Loads in a table from `file`, stores it into `data[<name>]`.  See summarize*table(::Val{:annual*cf_lim})
  * `modify_model!` - sets up the following constraints and expressions

      * Sets up expression `model[:egen_gen_annual]` (ngen x nhr) for annual energy generation for each generator
      * Creates constraint `model[:cons_<name>_min]` for each generator covered by each row of the table specified in `file`, if the `annual_cf_min` column is given.
      * Creates constraint `model[:cons_<name>_max]` for each generator covered by each row of the table specified in `file`, if the `annual_cf_max` column is given.
