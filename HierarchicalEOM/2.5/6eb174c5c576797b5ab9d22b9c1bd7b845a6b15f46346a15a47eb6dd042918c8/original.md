```
correlation_function(bath, tlist)
```

Calculate the correlation function $C(t)$ for a given bosonic bath and time list.

## if the input bosonic bath did not apply rotating wave approximation (RWA)

$$
C(t)=\sum_{u=\textrm{R},\textrm{I}}(\delta_{u, \textrm{R}} + i\delta_{u, \textrm{I}})C^{u}(t)
$$

where

$$
C^{u}(t)=\sum_i \eta_i^u e^{-\gamma_i^u t}
$$

## if the input bosonic bath applies rotating wave approximation (RWA)

$$
C^{\nu=\pm}(t)=\sum_i \eta_i^\nu e^{-\gamma_i^\nu t}
$$

# Parameters

  * `bath::BosonBath` : The bath object which describes a certain bosonic bath.
  * `tlist::AbstractVector`: The specific time.

# Returns (without RWA)

  * `clist::Vector{ComplexF64}` : a list of the value of correlation function according to the given time list.

# Returns (with RWA)

  * `cplist::Vector{ComplexF64}` : a list of the value of the absorption ($\nu=+$) correlation function according to the given time list.
  * `cmlist::Vector{ComplexF64}` : a list of the value of the emission ($\nu=-$) correlation function according to the given time list.
