```
TimeStepTable{Status}(df::DataFrame)
```

Method to build a `TimeStepTable` (from [PlantMeteo.jl](https://palmstudio.github.io/PlantMeteo.jl/stable/))  from a `DataFrame`, but with each row being a `Status`.

# Note

[`ModelList`](@ref) uses `TimeStepTable{Status}` by default (see examples below).

# Examples

```julia
using PlantSimEngine, DataFrames

# A TimeStepTable from a DataFrame:
df = DataFrame(
    Tₗ=[25.0, 26.0],
    aPPFD=[1000.0, 1200.0],
    Cₛ=[400.0, 400.0],
    Dₗ=[1.0, 1.2],
)
TimeStepTable{Status}(df)

# A leaf with several values for at least one of its variable will automatically use 
# TimeStepTable{Status} with the time steps:
models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model(),
    status=(var1=15.0, var2=0.3)
)

# The status of the leaf is a TimeStepTable:
status(models)

# Of course we can also create a TimeStepTable with Status manually:
TimeStepTable(
    [
        Status(Tₗ=25.0, aPPFD=1000.0, Cₛ=400.0, Dₗ=1.0),
        Status(Tₗ=26.0, aPPFD=1200.0, Cₛ=400.0, Dₗ=1.2),
    ]
)
```
