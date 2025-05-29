```
struct ExogenousInputs
    intervention::Dict{Symbol, Dict}
    temperature::Dict{Symbol, Float64}
    function ExogenousInputs(;
        intervention = Dict{Symbol, Dict}(),
        temperature = Dict{Symbol, Float64}())
        new(intervention,
        temperature)
    end
end
```

Data for perturbations to the simulated system, including (1) biological control interventions and (2) externally defined temperature series/shocks.
