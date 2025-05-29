```julia
predictVariableByFactor(dfg, targetsym, fct, prevars)

```

Method to compare current and predicted estimate on a variable, developed for testing a new factor before adding to the factor graph.

Notes

  * `fct` does not have to be in the factor graph – likely used to test beforehand.
  * function is useful for detecting if `multihypo` should be used.
  * `approxConv` will project the full belief estimate through some factor but must already be in factor graph.

Example

```julia
# fg already exists containing :x7 and :l3
pp = Pose2Point2BearingRange(Normal(0,0.1),Normal(10,1.0))
# possible new measurement from :x7 to :l3
curr, pred = predictVariableByFactor(fg, :l3, pp, [:x7; :l3])
# example of naive user defined test on fit score
fitscore = minkld(curr, pred)
# `multihypo` can be used as option between existing or new variables
```

Related

approxConv
