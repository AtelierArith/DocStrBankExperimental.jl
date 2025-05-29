```
correlation_function(bath, tlist)
```

Calculate the correlation function $C^{\nu=+}(t)$ and $C^{\nu=-}(t)$ for a given fermionic bath and time list. Here, $\nu=+$ represents the absorption process and $\nu=-$ represents the emission process.

$$
C^{\nu=\pm}(t)=\sum_i \eta_i^\nu e^{-\gamma_i^\nu t}
$$

# Parameters

  * `bath::FermionBath` : The bath object which describes a certain fermionic bath.
  * `tlist::AbstractVector`: The specific time.

# Returns

  * `cplist::Vector{ComplexF64}` : a list of the value of the absorption ($\nu=+$) correlation function according to the given time list.
  * `cmlist::Vector{ComplexF64}` : a list of the value of the emission ($\nu=-$) correlation function according to the given time list.
