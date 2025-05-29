Accumulators can be used to calculate aggregate statistics over sets of elements. In order to be able to work with `@observe.@stat` an accumulator has to implement the following functions:

  * `add!(acc, dat)` - add a datum to the accumulator. This function has no default implementation.
  * `result_type(T)` - the type of the result the accumulator generates. Per default it is assumed that this is identical to the accumulator type itself.
  * `result(acc)` - obtain the current result from the accumulator. Returns the accumulator object itself by default.
