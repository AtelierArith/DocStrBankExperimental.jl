get*absorption*chiller*defaults(prime*mover::String, boiler*type::String, size*class::Int)

return a Dict{String, Any} by selecting the appropriate values from  data/chp/absorption*chiller*defaults.json, which contains values based on heat transfer medium (thermal*consumption*hot*water*or_steam) such as:

  * "installed*cost*per_ton"
  * "om*cost*per_ton"
  * "cop_thermal"
  * "tech*sizes*for*cost*data"

Unlike CHP, the AbsorptionChiller tech sizes inform a single rate for installed*cost*per*ton that uses max*ton as input; there is no piecewise linear cost curve for the AbsorptionChiller technology.

Inputs:  thermal*consumption*hot*water*or*steam::Union{String, Nothing} – identifier of chiller thermal consumption type (steam or hot water) chp*prime*mover::Union{String, Nothing} – identifier of CHP prime mover, if any  boiler*type::Union{String, Nothing} – identifier of boiler type (steam or hot water) load*max*tons::Union{Float64, Nothing} – maximum cooling load [ton]

response keys and descriptions: "thermal*consumption*hot*water*or*steam" – string indicator of heat transfer medium for absorption chiller "default*inputs" – Dict{string, Float64} containing default values for absorption chiller technology (see above)
