Handle renaming variable names for discrete structural simplification. Three cases: 

  * positive shift: do nothing
  * zero shift: x(t) => Shift(t, 0)(x(t))
  * negative shift: rename the variable
