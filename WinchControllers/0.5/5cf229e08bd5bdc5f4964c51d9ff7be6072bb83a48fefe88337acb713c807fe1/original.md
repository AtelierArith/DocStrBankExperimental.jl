```
macro limit(name, minmax, max=nothing)
```

Limit the value of a variable. 

Parameters:

  * name: the name of the scalar variable that shall be limited
  * minmax: if max is provided, this is the lower value to which the variable is clamped, otherwise it is the upper value
  * max: the upper value to which to limit the provided variable or nothing

Usage:

  * @limit x 1 4 # limits the value to the range    1 .. 4,  modifies x
  * @limit x 10  # limits the value to the range -inf .. 10, modifies x
