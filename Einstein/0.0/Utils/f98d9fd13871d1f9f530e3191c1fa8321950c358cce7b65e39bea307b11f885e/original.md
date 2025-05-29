```
SWSFun{TR<:AbstractFloat}()
(swsf::SWSFun{TR})(θ::TR)
coefficients(swsf::SWSFun)
```

Spherical-weighted spheroidal harmonics. The eigenvectors contain the $C$ coefficients in the equation:

$$
{}_s S_{\ell m}(x; c)=\sum_{\ell^{\prime}=\ell_{\min }}^{\infty} C_{\ell^{\prime} \ell m}(c) {}_s S_{\ell^{\prime} m}(x; 0)
$$

where $C$ is normalized by

$$
\sum_{\ell^{\prime}=\ell_{\text {min }}}^{\ell_{\max }}\left|C_{\ell^{\prime} \ell m}(c)\right|^2=1
$$

and the phase is chosen such that $C_{\ell^{\prime} \ell m}(c)$ is real for $\ell^{\prime}=\ell$ [Cook:2014cta](@cite). The spin-weighted spheroidal harmonics are normalized such that

$$
\int_0^\pi {}_s S_{\ell m}(x; c) {}_s S^*_{\ell m}(x; c) \sin(\theta) d\theta = 1
$$

# Arguments

  * `s::Integer`: spin
  * `c::Complex{TR}`: oblateness parameter
  * `m::Integer`: azimuthal number
  * `l::Integer`: angular number
  * `l_max::Integer`: maximum angular number
