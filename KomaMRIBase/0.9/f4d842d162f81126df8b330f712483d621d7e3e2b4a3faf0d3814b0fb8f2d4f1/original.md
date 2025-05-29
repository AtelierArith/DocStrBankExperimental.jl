```
t = times(gr::Grad)
t = times(rf::RF)
t = times(adc::ADC)
```

Get time samples of MRI sequence event.

# Arguments

  * `gr`: (`::Grad`) Gradient struct
  * `rf`: (`::RF`) RF struct
  * `adc`: (`::ADC`) ADC struct

# Returns

  * `t`: (`::Vector{Number}`) vector with time samples
