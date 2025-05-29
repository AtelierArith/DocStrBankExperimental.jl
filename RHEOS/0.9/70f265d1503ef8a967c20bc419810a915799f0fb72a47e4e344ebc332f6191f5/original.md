```
lossmod(m[, ω, params])
```

provide access to the loss modulus (G'') of a given model m.

When a frequency value is provided (or an array of frequency values), the function returns the corresponding value(s) of the loss modulus.

```
lossmod(m::RheoModel, frequency (single value or array))

lossmod(m::RheoModelClass, frequency (single value or array), parameters (array, named tupple or keyword parameters))
```

Examples:

```
lossmod(Maxwell, 1, k=1., η=1)

lossmod(Maxwell, [1,2,3], [1,1])
```

When no time value is provided, lossmod returns the loss modulus function itself.

```
lossmod(m::RheoModel)

lossmod(m::RheoModelClass, parameters (array, named tupple or keyword parameters))
```

Examples:

```
m = RheoModel(Maxwell, k=1., η=1)
Gpp = lossmod(m)
Gpp([0,1,2])
```
