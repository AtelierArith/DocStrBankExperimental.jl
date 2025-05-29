```
storagemod(m[, ω, params])
```

provide access to the storage modulus (G') of a given model m.

When a frequency value is provided (or an array of frequency values), the function returns the corresponding value(s) of the storage modulus.

```
storagemod(m::RheoModel, frequency (single value or array))

storagemod(m::RheoModelClass, frequency (single value or array), parameters (array, named tupple or keyword parameters))
```

Examples:

```
storagemod(Maxwell, 1, k=1., η=1)

storagemod(Maxwell, [1,2,3], [1,1])
```

When no time value is provided, storagemod returns the storage modulus function itself.

```
storagemod(m::RheoModel)

storagemod(m::RheoModelClass, parameters (array, named tupple or keyword parameters))
```

Examples:

```
m = RheoModel(Maxwell, k=1., η=1)
Gp = storagemod(m)
Gp([0,1,2])
```
