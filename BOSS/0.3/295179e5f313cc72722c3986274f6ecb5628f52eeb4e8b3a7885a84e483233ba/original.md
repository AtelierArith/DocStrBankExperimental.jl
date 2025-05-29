```
x = maximize_acquisition(::BossProblem, ::AcquisitionFunction, ::AcquisitionMaximizer)
```

Maximize the given `acquisition` function via the given `acq_maximizer` algorithm to find the optimal next evaluation point(s).

# Keywords

  * `options::BossOptions`: Defines miscellaneous settings.
