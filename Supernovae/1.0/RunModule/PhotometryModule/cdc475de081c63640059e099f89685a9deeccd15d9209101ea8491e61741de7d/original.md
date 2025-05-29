```
mag_to_absmag(mag::Level, redshift::Float64; H0::Unitful.Quantity{Float64}=70.0u"km/s/Mpc")
```

Converts `mag` to absolute magnitude. Calculates `mag - 5 log10(c * redshift / (H0 * 10pc))`

# Arguments

  * `mag::Level`: The magnitude to convert
  * `redshift::Float64`: The redshift, used to calculate the distance to the object
  * `;H0::Unitful.Quantity{Float64}=70.0u"km/s/Mpc`: The assumed value of H0, used to calculate the distance to the object
