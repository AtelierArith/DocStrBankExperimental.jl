```
struct CCUS <: Modification

CCUS(;file, groupby, co2_scalar=1e5, co2_step_quantity_limit=1e9)
```

This is a [`Modification`](@ref) that sets up markets for carbon captured by generators.  

  * `file` - a file to the table containing markets/prices for buying/selling carbon dioxide.  See the `ccus_paths` table below, or [`summarize_table(::Val{:ccus_paths})`](@ref)
  * `groupby` - a `String` indicating how markets are grouped.  I.e. "state".
  * `co2_scalar` - a `Float64` for how much to scale the co2 variables by.  This helps with numerical instability, given that some CO₂ steps can be very large and could bloat the RHS and bounds range of the model.  A good rule of thumb is that this should be no less than `1e4` times smaller than `co2_step_quantity_limit`.
  * `co2_step_quantity_limit` - A `Float64` for the maximum quantity of CO₂ that can be stored in any step.

Creates the following tables in `data`:

  * `ccus_paths` - contains all pathways possible to sell CO₂.  

      * `producing_region` - The producing region
      * `storing_region` - The storing region of the pathway
      * `ccus_type` - the type of ccus (`eor` or `saline`)
      * `step_id` - the number of the step (not very important other than for book-keeping)
      * `step_quantity` - the quantity of CO₂ that can be stored in this step
      * `price_trans` - the cost to transport 1 short ton of CO₂ from `producing_region` to `storing_region`
      * `price_store` - the cost to store 1 short ton of CO₂ in the step
  * `ccus_storers` - contains all the storers

      * `storing_region` - the storing region
      * `step_id` - the number of the step for the region
      * `ccus_type` - whether the step is `eor` or `saline`.
      * `step_quantity` - the number of short tons that may be stored in the step
      * `price_store` - the price to store a short ton of CO₂.
      * `path_idxs` - A list of indices representing the transportation paths to store carbon in this step.  Indexes into `ccus_paths` table.
  * `ccus_producers` - contains all the producers, grouped by `ccus_type` and `producing_region`.  This contains the following columns:

      * `producing_region` - the region the CO₂ will be sent from
      * `ccus_type` - the type of the step the CO₂ will be sent to (`eor` or `saline`)
      * `path_idxs` - A list of indices representing the transportation paths to send carbon from this step.  Indexes into `ccus_paths` table.
      * `gen_idxs` - A list of generator indices that produce CO₂ in this region.

Creates the following variables/expressions

  * `co2_trans[1:nrow(ccus_paths), 1:nyear]` - the amount of CO₂ transported along this producer-producer pathway (variable)
  * `co2_stor[1:nrow(ccus_storers), 1:nyear]` - the amount of CO₂ stored by each storer (expression of `co2_trans`)
  * `co2_prod[1:nrow(ccus_producers), 1:nyear]` - the amount of CO₂ produced by each sending region (expression of electricity generation)
  * `co2_sent[1:nrow(ccus_producers), 1:nyear]` - the amount of CO₂ sent out from each sending region (expression of `co2_trans`).  This includes CO₂ sent within the same region.
  * `cost_ccus_obj[1:nyear]` - the total cost of ccus, as added to the objective function.

Creates the following constraints

  * `cons_co2_stor[1:nrow(ccus_storers), 1:nyear]` - the CO₂ stored at each injection site must not exceed `step_quantity`
  * `cons_co2_bal[1:nrow(ccus_producers), 1:nyear]` - the CO₂ balancing equation for each region, i.e. `co2_prod == co2_sent`.

## Accessing Results

Results are stored in 2 places; the `ccus_paths` table, and the `gen` table.

Example Result Queries

  * `compute_result(data, :gen, :stored_co2_total, :ccus_type=>"eor", "y2030")`
  * `compute_result(data, :gen, :cost_capt_co2, :ccus_type=>"eor", yr_idx)`
  * `compute_result(data, :gen, :cost_capt_co2_store, :gentype=>"coalccs", yr_idx)`
  * `compute_result(data, :gen, :cost_capt_co2_trans, :, yr_idx)`
  * `compute_result(data, :ccus_paths, :storer_cost_total, :storing_region=>"narnia")`
  * `compute_result(data, :ccus_paths, :storer_revenue_total, :producing_region=>"narnia")`
  * `compute_result(data, :ccus_paths, :storer_profit_total, :ccus_type=>"eor")`

See also:

  * [`modify_raw_data!(::CCUS, config, data)`](@ref)
  * [`modify_setup_data!(::CCUS, config, data)`](@ref)
  * [`modify_model!(::CCUS, config, data, model)`](@ref)
  * [`modify_results!(::CCUS, config, data)`](@ref)
