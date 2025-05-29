```
dynamicmod(m[, ω, params])
```

provide access to the complex dynamic modulus (G' + i G'') of a given model m.

  * When a frequency value is provided (or an array of frequency values), the function returns the corresponding value(s) of the complex dynamic modulus.

    dynamicmod(m::RheoModel, frequency (single value or array))

    dynamicmod(m::RheoModelClass, frequency (single value or array), parameters (array, named tupple or keyword parameters))

Examples:

```
dynamicmod(Maxwell, 1, k=1., η=1)

dynamicmod(Maxwell, [1,2,3], [1,1])
```

  * When no time value is provided, lossmod returns the complex dynamic modulus function itself.

    dynamicmod(m::RheoModel)

    dynamicmod(m::RheoModelClass, parameters (array, named tupple or keyword parameters))

Examples:

```
m = RheoModel(Maxwell, k=1., η=1)
Gd = dynamicmod(m)
Gd([0,1,2])
```

Note: use abs() and angle() to get the magnitude and phase of the complex modulus.
