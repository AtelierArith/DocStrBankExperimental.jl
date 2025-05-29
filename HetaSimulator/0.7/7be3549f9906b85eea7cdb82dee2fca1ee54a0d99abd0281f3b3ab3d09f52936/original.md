struct Scenario{F,P,M} <: AbstractScenario     init_func::F     prob::P     measurements::M     tags::AbstractVector{Symbol}     group::Union{Symbol,Nothing}     parameters::NamedTuple   end

Type representing simulation conditions, i.e. model variant with updated parameters and outputs.

To get the internal properties use methods: `tspan(scenario)`, `parameters(scenario)`, `measurements(scenario)`
