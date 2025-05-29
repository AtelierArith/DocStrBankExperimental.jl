The differentation function returns an operator that can be used to differentiate a function in the dictionary, with the result as an expansion in a second dictionary.

The differentiation operator is efficient for some combinations of source and destination dictionary. If a dictionary supports at least one differentiation operator, than `hasderivative(dict)` is true and `derivative_dict(dict)` returns the destination dictionary.

The order of the differentation can be passed as an optional second argument.

Examples are:

```
differentiation(Φ::Dictionary)
```

This will use the default destination dictionary, order 1 and dimension 1. Another example is:

```
differentiation(Φ, 1)
```

or

```
differentiation(Φ, (0,1))
```
