```
departure_functions(model::MultiFluid)
```

if the model is using a `EmpiricDeparture` departure model, return the matrix of departure functions. you can set a departure in the following way:

```
using CoolProp #load CoolProp models
model = MultiFluid(["helium","methanol"],mixing = LorentzBerthelotMixing)
dep_mat = departure_functions(model)

dep = Dict(
    #reduced CoolProp Departure format, you only need the type and parameters.
    #ResidualHelmholtzPower would work too.
    type => "Exponential",
    n => [1,1,1,1],
    t => [1,1,1,1],
    d => [1,1,1,1],
    l => [1,1,1,1],
)


dep_mat[1,2] = create_departure(dep,F)

#if you want to delete a departure model:

dep_mat[1,2] = nothing
using SparseArrays
```
