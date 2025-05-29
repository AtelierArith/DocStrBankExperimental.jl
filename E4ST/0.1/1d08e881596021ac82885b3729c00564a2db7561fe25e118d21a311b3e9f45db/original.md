```
add_results_formula!(data, table_name::Symbol, result_name::Symbol, formula::String, unit::Type{<:Unit}, description::String)
```

Adds a formula that can be used to compute results.  See [`compute_result`](@ref).  This is also used by [`AggregationTemplate`](@ref) and [`YearlyTable`](@ref).

Arguments:

  * `data`
  * `table_name` - the name of the table that the result is calculated from, either directly or as a combination of other results
  * `result_name` - the name of the result being calculated.  Cannot be a column name within the table.
  * `formula` - `formula` can take two different forms.

      * it can be a combination of columns to be aggregated directly from `table_name`.  I.e. `"SumHourly(vom, egen)"`. See [`Sum`](@ref), [`SumHourly`](@ref), [`SumYearly`](@ref), [`AverageYearly`](@ref), [`MinHourly`](@ref).  Note that the columns here can either be column names or variable names stored with `data`, like `dam_co2`
      * it can also be a combination of other results. I.e. `"(vom_cost + fuel_cost) / egen_total"`.
  * `unit` - the [`Unit`](@ref) of the resulting number
  * `description` - a short description of the calculation.
