```
ParameterBounds(ids::Vector{Integer},lbs::Vector{Number},ubs::Vector{Number})
```

parameters[ids] must fall within lbs and ubs, where lbs and ubs are Arrays of the same size as ids. Create hard bounds on the parameter space over which the minimally disruptive curve can trace. Curve evolution terminates if it hits a bound.
