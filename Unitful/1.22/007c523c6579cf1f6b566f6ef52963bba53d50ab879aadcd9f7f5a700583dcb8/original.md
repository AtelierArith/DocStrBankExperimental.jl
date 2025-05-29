```
linear(x::Quantity)
linear(x::Level)
linear(x::Number) = x
```

Returns a quantity equivalent to `x` but without any logarithmic scales.

It is important to note that this operation will error for `Quantity{<:Gain}` types. This is for two reasons:

  * `20dB` could be interpreted as either a power or root-power ratio.
  * Even if `-20dB/m` were interpreted as, say, `0.01/m`, this means something fundamentally different than `-20dB/m`. `0.01/m` cannot be used to calculate exponential attenuation.
