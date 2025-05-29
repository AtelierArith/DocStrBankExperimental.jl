```
LNS{TMethodSelector <: MethodSelector, TSolution <: Solution}
```

A basic large neighborhood search.

Attributes

  * `solution`: current solution
  * `scheduler`: `Scheduler`
  * `meths_ch`: list of construction heuristic methods
  * `meths_de`: list of destroy methods
  * `meths_re`: list of repair methods
  * `meths_compat`: Boolean matrix indicating which destroy method can be applied   in conjunction with which repair method, i.e., `meths_compat[i,j]==true` indicates   that the i-th destroy method can be applied with the j-th repair method
  * `temperature`: temperature for Metropolis criterion
  * `params`: LNSParameters, by default adopted from global settings
