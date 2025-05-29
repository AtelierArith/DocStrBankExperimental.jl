```
Kubo{K<:Union{Nothing, Vector{Float64}}} <: BerryCurvatureMethod
```

Kubo method to calculate the total Berry curvature of occupied energy bands. The Kubo formula is given by

$$
\Omega_{ij}(\bm k)=\epsilon_{ijl}\sum_{n}f(\epsilon_n(\bm k))b_n^l(\bm k)=-2{\rm Im}\sum_v\sum_c{V_{vc,i}(\bm k)V_{cv,j}(\bm k)\over [\omega_c(\bm k)-\omega_v(\bm k)]^2},
$$

where

$$
 V_{cv,j}={\langle u_{c\bm k}|{\partial H\over \partial {\bm k}_j}|u_{v\bm k}\rangle}
$$

v and c subscripts denote valence (occupied) and conduction (unoccupied) bands, respectively. Hall conductivity in 2D space is given by

$$
\sigma_{xy}=-{e^2\over h}\int_{BZ}{dk_x dk_y\over 2\pi}{\Omega_{xy}}
$$
