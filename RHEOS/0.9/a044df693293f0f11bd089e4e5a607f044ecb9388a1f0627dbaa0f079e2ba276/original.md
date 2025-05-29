```
relaxmod(m[, t, params])
```

provide access to the relaxation modulus (G) of a given model m. It can be used with a broad range of inputs.

When a time value is provided (or an array of time values), the function returns the corresponding value(s) of the relaxation modulus.

```
relaxmod(m::RheoModel, time (single value or array))

relaxmod(m::RheoModelClass, time (single value or array), parameters (array, named tupple or keyword parameters))
```

Examples:

```
relaxmod(Maxwell, 1, k=1., η=1)

relaxmod(Maxwell, [1,2,3], [1,1])
```

When no time value is provided, relaxmod returns the relaxation function itself.

```
relaxmod(m::RheoModel)

relaxmod(m::RheoModelClass, parameters (array, named tupple or keyword parameters))
```

Examples:

```
m = RheoModel(Maxwell, k=1., η=1)
G = relaxmod(m)
G([0,1,2])
```
