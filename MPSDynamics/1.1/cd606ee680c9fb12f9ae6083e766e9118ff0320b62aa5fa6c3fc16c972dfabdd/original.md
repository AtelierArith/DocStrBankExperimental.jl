```
chaincoeffs_finiteT(nummodes, β, ohmic=true; α, s, J, ωc=1, mc=4, mp=0, AB=nothing, iq=1, idelta=2, procedure=:Lanczos, Mmax=5000, save=true)
```

Generate chain coefficients $[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$ for a harmonic bath at the inverse temperature β.

By default a Ohmic spectral density $J(ω) = 2αω_c (\frac{ω}{ω_c})^s θ(ω-ω_c)$ is considered. Users can provide their own spectral density.

# Arguments

  * nummodes: Number of bath modes
  * β: inverse temperature
  * ohmic: true if the spectral density is Ohmic, false if the user provides its own spectral density
  * α: Kondo parameter of the Ohmic spectral density
  * s: ohmicity
  * J: user-provided spectral density. Should be a function f(x,i) where x is the frequency and i ∈ {1,...,mc} labels the intervals on which the SD is defined
  * ωc: the maximum frequency of the Ohmic spectral density
  * mc: the number of component intervals
  * mp: the number of points in the discrete part of the measure (mp=0 if there is none)
  * iq: a parameter to be set equal to 1, if the user provides his or her own quadrature routine, and different from 1 otherwise
  * idelta: a parameter whose default value is 1, but is preferably set equal to 2, if iq=1 and the user provides Gauss-type quadrature routines
  * procedure: choice between the Stieltjes and the Lanczos procedure
  * AB: component intervals
  * Mmax: maximum number of integration points
  * save: if true the coefficients are saved
