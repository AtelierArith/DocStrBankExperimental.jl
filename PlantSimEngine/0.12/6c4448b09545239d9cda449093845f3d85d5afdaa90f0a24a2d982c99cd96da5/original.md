```
convert_outputs(sim_outputs::Dict{String,O} where O, sink; refvectors=false, no_value=nothing)
convert_outputs(sim_outputs::TimeStepTable{T} where T, sink)
```

Convert the outputs returned by a simulation made on a plant graph into another format.

# Details

The first method operates on the outputs of a multiscale simulation, the second one on those of a typical single-scale simulation.  The sink function determines the format used, for exemple a `DataFrame`.

# Arguments

  * `sim_outputs : the outputs of a prior simulation, typically returned by`run!`.
  * `sink`: a sink compatible with the Tables.jl interface (*e.g.* a `DataFrame`)
  * `refvectors`: if `false` (default), the function will remove the RefVector values, otherwise it will keep them
  * `no_value`: the value to replace `nothing` values. Default is `nothing`. Usually used to replace `nothing` values

by `missing` in DataFrames.

# Examples

```@example
using PlantSimEngine, MultiScaleTreeGraph, DataFrames, PlantSimEngine.Examples
```

Import example models (can be found in the `examples` folder of the package, or in the `Examples` sub-modules): 

```jldoctest mylabel
julia> using PlantSimEngine.Examples;
```

```@example
mapping = Dict( "Plant" =>  ( MultiScaleModel(  model=ToyCAllocationModel(), mapped_variables=[ :carbon_assimilation => ["Leaf"], :carbon_demand => ["Leaf", "Internode"], :carbon_allocation => ["Leaf", "Internode"] ], ), 
        MultiScaleModel(  model=ToyPlantRmModel(), mapped_variables=[:Rm_organs => ["Leaf" => :Rm, "Internode" => :Rm],] ), ),"Internode" => ( ToyCDemandModel(optimal_biomass=10.0, development_duration=200.0), ToyMaintenanceRespirationModel(1.5, 0.06, 25.0, 0.6, 0.004), Status(TT=10.0) ), "Leaf" => ( MultiScaleModel( model=ToyAssimModel(), mapped_variables=[:soil_water_content => "Soil",], ), ToyCDemandModel(optimal_biomass=10.0, development_duration=200.0), ToyMaintenanceRespirationModel(2.1, 0.06, 25.0, 1.0, 0.025), Status(aPPFD=1300.0, TT=10.0), ), "Soil" => ( ToySoilWaterModel(), ), )
```

```@example
mtg = import_mtg_example();
```

```@example
out = run!(mtg, mapping, meteo, tracked_outputs = Dict(
    "Leaf" => (:carbon_assimilation, :carbon_demand, :soil_water_content, :carbon_allocation),
    "Internode" => (:carbon_allocation,),
    "Plant" => (:carbon_allocation,),
    "Soil" => (:soil_water_content,),
));
```

```@example
convert_outputs(out, DataFrames)
```
