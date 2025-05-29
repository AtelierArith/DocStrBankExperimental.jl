```
diffProjection(u::Matrix{Float64}, σ::Matrix{Float64}, v::Matrix{Float64};
s::Integer, L::Integer, m::Integer, q::Integer)

UNTESTED 

projects diffusions eigenfunctions to physical space using linear op components from SVD
(i.e. results of diffSVD), from appendix of 10.1073/pnas.1118984109

Arguments
=================
- u, σ, v: from diffSVD(), i.e. [u, σ, v] = diffSVD()

Keyword arguments
=================
- s: number of samples for which temporal modes are computed
- L: number of computed diffusion eigenfunctions
- m: physical space dimension
- q: number of delays (no delays means q = 1)
```
