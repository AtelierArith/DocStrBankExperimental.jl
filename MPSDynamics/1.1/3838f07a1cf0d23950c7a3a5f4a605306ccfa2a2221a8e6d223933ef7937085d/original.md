chaincoeffs_fermionic(nummodes, β, chain; ϵ=nothing, J=nothing, ωc=1, mc=4, mp=0, AB=nothing, iq=1, idelta=2, procedure=:Lanczos, Mmax=5000, save=true)

Generate chain coefficients $[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$ for a fermionic bath at the inverse temperature β.

# Arguments

  * nummodes: Number of bath modes
  * β: inverse temperature
  * chain: 1 if the chain modes are empty, 2 if the chain modes are filled
  * ϵ: user-provided dispersion relation. Should be a function f(x) where x is the wavenumber
  * J: user-provided spectral density. Should be a function f(x) where x is the wavenumber
  * ωc: the maximum frequency allowwed in the spectral density
  * mc: the number of component intervals
  * mp: the number of points in the discrete part of the measure (mp=0 if there is none)
  * iq: a parameter to be set equal to 1, if the user provides his or her own quadrature routine, and different from 1 otherwise
  * idelta: a parameter whose default value is 1, but is preferably set equal to 2, if iq=1 and the user provides Gauss-type quadrature routines
  * procedure: choice between the Stieltjes and the Lanczos procedure
  * AB: component intervals
  * Mmax: maximum number of integration points
  * save: if true the coefficients are saved
