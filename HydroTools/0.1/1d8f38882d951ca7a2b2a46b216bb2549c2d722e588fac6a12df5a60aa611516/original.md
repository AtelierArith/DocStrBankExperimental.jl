```
cal_Rn(Rs, Rln, Tavg, albedo, emiss)
```

Calculate net radiation (Rn) using input parameters.

# Arguments

  * `Rs`   : Shortwave inward solar radiation, W m-2.
  * `Rln`  : Longwave inward solar radiation, W m-2.
  * `Tavg` : Average temperature in Celsius.
  * `α`    : Shortwave albedo.
  * `ϵ`    : Longwave emissivity.

# Returns

  * `Rn`: Net radiation, W m-2.

# Example

```julia
cal_Rn(20.0, 20, 20., 25., 2.0, 10.0)
```
