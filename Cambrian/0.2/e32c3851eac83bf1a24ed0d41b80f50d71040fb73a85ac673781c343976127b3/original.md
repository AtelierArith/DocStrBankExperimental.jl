Every AbstractEvolution subclass needs to have the following fields:     config::NamedTuple     logger::CambrianLogger     population::Array{<:Individual} for config, see get*default*config

Evolution classes should implement the following methods:     populate(e::Evolution)     evaluate(e::Evolution)     generation(e::Evolution) see the default functions for reference
