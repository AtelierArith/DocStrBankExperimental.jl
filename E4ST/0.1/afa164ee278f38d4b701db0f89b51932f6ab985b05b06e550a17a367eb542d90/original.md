```
CoalCCSRetrofit(;kwargs...) <: Retrofit
```

`CoalCCSRetrofit` represents a [`Retrofit`](@ref) for changing coal-burning plants (gentype="coal"), to have carbon capture technology, and be changed to (gentype="coal*ccsus*retrofit")

Keyword Arguments:

  * `crf = 0.115642438` - the capital recovery factor (default value assumes 12 year economic lifetime)
  * `capt_co2_percent = 0.9` - (between 0 and 1) the percentage of CO₂ captured by the retrofit
  * `reduce_nox_percent =  0.25` - (between 0 and 1) the percent reduction in NOₓ emissions (default is midpoint of 0% and 50% reduction)
  * `reduce_so2_percent = 0.985` - (between 0 and 1) the percent reduction in SO₂ emissions (default is midpoint of 97% and 100% reduction)
  * `reduce_pm25_percent = 0.33` - (between 0 and 1) the percent reduction in PM2.5 emissions (default is midpoint of -4% and 70% reduction)
  * `econ_life = 12.0` - the assumed economic life of the retrofit.  Moves out the planned year*shutdown to be at the end of the retrofit economic lifetime if year*shutdown is earlier than the end of the econ life.

Other Requirements:

  * The `gen` table must have a `heat_rate` column
  * The `gen` table must either have a `pcap_plant_avg` column, or it will be assumed that each generator represents a single plant.  This value is used with the cost curves.

Cost adjustment values come from a regression in EPA Schedule 6 data.
