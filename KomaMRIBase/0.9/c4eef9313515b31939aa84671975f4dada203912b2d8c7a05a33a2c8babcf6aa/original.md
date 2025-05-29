```
A = ampls(g::Grad)
A = ampls(r::RF)
A = ampls(d::ADC)
```

Get amplitude samples of MRI sequence event.

# Arguments

  * `gr`: (`::Grad`) Gradient struct
  * `rf`: (`::RF`) RF struct
  * `adc`: (`::ADC`) ADC struct

# Returns

  * `A`: (`::Vector{Number}`) vector with amplitude samples
