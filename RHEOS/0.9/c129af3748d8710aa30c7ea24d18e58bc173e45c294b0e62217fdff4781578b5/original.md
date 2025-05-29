```
RheoModel(m::RheoModelClass, nt0::NamedTuple)
```

`RheoModel` represents a rheological model with set parameters. They are obtained by fitting a model to data using `modelfit`,  or by specialising the relevant RheoModelClass by prescribing its parameters. Parameters can be provided as a named tuple or keyword arguments.

`RheoModel` objects can then be used to simulate the response to an arbitrary input using `modelpredict`, and access the values of the moduli functions.

# Example

```@example
julia> model = RheoModel(Maxwell, (k=1, η=2.))
[...]

julia> model = RheoModel(Maxwell, k=1, η=2.)
[...]
```
