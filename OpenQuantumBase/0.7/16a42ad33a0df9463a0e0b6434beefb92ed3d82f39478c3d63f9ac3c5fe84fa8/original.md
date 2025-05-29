```julia
struct HybridOhmicBath <: OpenQuantumBase.AbstractBath
```

A hybrid noise model with both low and high frequency noise. The high frequency noise is characterized by Ohmic bath and the low frequence noise is characterized by the MRT width `W`.

  * `W`: MRT width (2π GHz)
  * `ϵl`: low spectrum reorganization energy (2π GHz)
  * `η`: strength of high frequency Ohmic bath
  * `ωc`: cutoff frequency
  * `β`: inverse temperature
