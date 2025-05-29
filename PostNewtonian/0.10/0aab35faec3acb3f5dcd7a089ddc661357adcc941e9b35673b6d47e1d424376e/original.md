```
h!(h, pnsystem; ℓₘᵢₙ=0, ℓₘₐₓ=typemax(Int))
mode_weights!(h, pnsystem; ℓₘᵢₙ=0, ℓₘₐₓ=typemax(Int))
```

Compute mode weights of gravitational waves emitted by `pn` system, modifying `h` in place.

!!! note
    This is a low-level function; you probably don't want to use this directly.  See [`coorbital_waveform`](@ref) or [`inertial_waveform`](@ref) for more user-friendly functions.


These modes are computed in the "co-orbital" frame, in which the larger object lies on the positive $x$ axis, the smaller lies on the negative $x$ axis, and the instantaneous angular velocity is in the positive $z$ direction.

The modes are stored in `h` in order of increasing $ℓ$ and increasing $m$, with $m$ iterating fastest, all the way up to the highest available mode, $(8,8)$.

Because gravitational waves have spin weight -2, the $(ℓ,m)=(0,0)$, $(1,-1)$, $(1,0)$, and $(1,1)$ modes are always 0.  By default, we assume that these modes are nonetheless included in `h`.  If that is not the case, set `ℓₘᵢₙ` to the smallest $ℓ$ value that should be present in the output data — `ℓₘᵢₙ=2` being the most reasonable alternative.

These results come most directly from Eqs. (A5) of [Boyle et al. (2014)](https://arxiv.org/abs/1409.4431), with the exception of errors in the 2PN spin-spin terms, in which cases we must multiply by $\nu/2$ and make the substitutions $S_1 \mapsto S_0^+$ and $S_2 \mapsto S_0^-$.  In turn, those expressions are synthesized from the following:  Non-spinning terms are taken from [Blanchet (2014)](https://doi.org/10.12942/lrr-2014-2), except for the highest-pN term in the (2,±2) mode, which are taken from [Blanchet et al.  (2023)](https://arxiv.org/abs/2304.11186), and the $m=0$ modes, which are taken from [Favata (2008)](https://arxiv.org/abs/0812.0069). The 1PN spin-orbit term is from Eq. (3.22d) of [Kidder (1995)](https://link.aps.org/doi/10.1103/PhysRevD.52.821).  The 1.5PN spin-orbit term is from Eq. (3.22f) of Kidder (1995) and Eq. (F15b) of [Will and Wiseman (1996)](https://link.aps.org/doi/10.1103/PhysRevD.54.4813).  The 2PN spin-orbit term is from Eq. (4.13) of [Buonanno, Faye, Hinderer (2013)](https://link.aps.org/doi/10.1103/PhysRevD.87.044009), while the 2PN spin-spin term is from Eq. (4.15) of that reference.
