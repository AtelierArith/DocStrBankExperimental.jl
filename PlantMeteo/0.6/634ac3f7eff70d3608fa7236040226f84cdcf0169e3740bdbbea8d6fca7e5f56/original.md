```
TimeStepTable(vars)
```

`TimeStepTable` stores variables values for each time step, *e.g.* weather variables. It implements the `Tables.jl` interface, so it can be used with any package that uses  `Tables.jl` (like `DataFrames.jl`).

You can extend `TimeStepTable` to store your own variables by defining a new type for the  storage of the variables. You can look at the [`Atmosphere`](@ref) type  for an example implementation, or the `Status` type from  [`PlantSimEngine.jl`](https://github.com/VEZY/PlantSimEngine.jl).

# Examples

```julia
data = TimeStepTable(
    [
        Atmosphere(T = 20.0, Wind = 1.0, P = 101.3, Rh = 0.65),
        Atmosphere(T = 23.0, Wind = 1.5, P = 101.3, Rh = 0.60),
        Atmosphere(T = 25.0, Wind = 3.0, P = 101.3, Rh = 0.55)
    ]
)

# We can convert it into a DataFrame:
using DataFrames
df = DataFrame(data)

# We can also create a TimeStepTable from a DataFrame:
TimeStepTable(df)

# Note that by default it will use NamedTuple to store the variables
# for high performance. If you want to use a different type, you can
# specify it as a type parameter (if you want *e.g.* mutability or pre-computations):
TimeStepTable{Atmosphere}(df)
# Or if you use PlantSimEngine: TimeStepTable{Status}(df)
```
