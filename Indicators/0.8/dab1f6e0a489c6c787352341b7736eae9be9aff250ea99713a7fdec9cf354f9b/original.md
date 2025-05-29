```
psar(hl::Array{T}; af_min::T=0.02, af_max::T=0.2, af_inc::T=af_min)::Array{Float64}
```

Parabolic stop and reverse (SAR)

*Arguments*

  * `hl`: 2D array of high and low prices in first and second columns respectively
  * `af_min`: starting/initial value for acceleration factor
  * `af_max`: maximum acceleration factor (accel factor capped at this value)
  * `af_inc`: increment to the acceleration factor (speed of increase in accel factor)
