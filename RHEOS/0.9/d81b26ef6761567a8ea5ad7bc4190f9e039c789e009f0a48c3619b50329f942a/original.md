```
creepcomp(m[, t, params])
```

provide access to the creep compliance (J) of a given model m. It can be used with a broad range of inputs.

When a time value is provided (or an array of time values), the function returns the corresponding value(s) of the creep compliance.

```
creepcomp(m::RheoModel, time (single value or array))

creepcomp(m::RheoModelClass, time (single value or array), parameters (array, named tupple or keyword parameters))
```

Examples:

```
creepcomp(Maxwell, 1, k=1., η=1)

creepcomp(Maxwell, [1,2,3], [1,1])
```

When no time value is provided, creepcomp returns the creep compliance function itself.

```
creepcomp(m::RheoModel)

creepcomp(m::RheoModelClass, parameters (array, named tupple or keyword parameters))
```

Examples:

```
m = RheoModel(Maxwell, k=1., η=1)
J = creepcomp(m)
J([0,1,2])
```
