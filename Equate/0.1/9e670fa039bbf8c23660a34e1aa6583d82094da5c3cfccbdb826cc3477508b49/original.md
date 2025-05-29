```
Equipercentile(X::EG, Y::EG; case = :middle)
```

Equipercentile Equating under equivalent (single) group design. The smoothed frequency can be used. A table returned by the function contains 2 columns. The first one stands for the base scale score in the test X. The second one is equated score from test Y, which is equipercentile score on the base scale.

`case` represents which equating case use. Pass to the symbols below.

  * `:upper` Calculating scores correspond to arbitrary percentile P, use the smallest integer score with a cumulative percent that is greater than P.
  * `:lower` (default) Contrary to above case, use the largest integer score with a cumulative percent that is less than P
  * `:both` (Not for practice) Show both case of upper and lower.
  * `:middle` Use midpoint case upper between lower.

In my example cases, it seems that equate package in R uses `lower` case to equate.
