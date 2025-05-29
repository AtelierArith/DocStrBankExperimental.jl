```
TransientStepData(dataset)
```

Container for data concerning a single transient sorption step. I.e., a profile of mass concentration with time (starting from a previous equilibrium and *generally* reaching a new equilibrium) of some penetrant into an even film of polymer material, or more succinctly, a *polymer slab*. 

# Arguments

  * `dataset`: Should be some iterable with 

      * the first item being an iterable of time data (in **seconds**)
      * the second item being an iterable of dimensionless sorption data (no units)
