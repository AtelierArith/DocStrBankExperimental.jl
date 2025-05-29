```
UniTrapezoid <: AbstractUnivariateMethod
```

An integral evalution method that uses the trapezoid rule to in combination with all parameter supports available when the integral is expanded and/or when the infinite model is optimized, whichever comes first. Note this method will ignore the `num_supports` keyword argument. The upper and lower bounds of the integral  will automatically be added as supports. Note this is valid only for finite integral domains. Contains no fields.
