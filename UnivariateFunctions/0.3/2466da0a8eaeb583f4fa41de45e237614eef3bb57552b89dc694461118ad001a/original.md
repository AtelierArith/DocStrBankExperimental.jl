```
trim_piecewise_function(func::Piecewise_Function, left_limit::Real, right_limit::Real)
```

This trims the end of a piecewise function. So if there is a piecewise function with support between -10,10 then you can trim it to only have support between -5 and 5. Then if it is evaluated outside -5 to 5 it will be undefined.

### Inputs

  * `func` - A Piecewise_Function.
  * `left_limit` - The left limit.
  * `right_limit` - The right limit.

### Returns

  * A `Piecewise_Function`.
