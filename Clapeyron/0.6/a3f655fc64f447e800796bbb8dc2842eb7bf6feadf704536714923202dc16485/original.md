```
create_departure(data,F = 1.0;verbose = false)
```

Creates a departure model for use in a `MultiFluid` model with `EmpiricDeparture`.

If `data` is a `String` and starts with `{` or `[`, it will be recognized as JSON text. the text will be parsed as a file location otherwise.  You can pass a `Dict` or `NamedTuple` if you want to skip the JSON parsing.

## Examples

```julia
d1 = create_departure("/data/EthanePropane.json",0.9) # reading from a file

dep = Dict(
    #reduced CoolProp Departure format, you only need the type and parameters.
    #ResidualHelmholtzPower would work too.
    :type => "Exponential",
    :n => [1,1,1,1],
    :t => [1,1,1,1],
    :d => [1,1,1,1],
    :l => [1,1,1,1],
)

d2 = create_departure(dep) #F is set to 1.0
```
