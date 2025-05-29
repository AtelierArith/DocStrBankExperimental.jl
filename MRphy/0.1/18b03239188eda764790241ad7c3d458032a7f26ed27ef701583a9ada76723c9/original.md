```
freePrec!(M, t; Δf=0u"Hz", T1=(Inf)u"s", T2=(Inf)u"s")
```

Spins, `M`, free precess by time `t`. `M` will be updated by the results.

*INPUTS*:

  * `M::TypeND(Real, [2])` (nM, xyz): input spins' magnetizations.
  * `t::T0D` (1,): duration of free precession.

*KEYWORDS*:

  * `T1 & T2 ::TypeND(T0D, [0,1])`: Global, (1,); Spin-wise, (nM,1).

*OUTPUTS*:

  * `M::TypeND(Real, [2])` (nM, xyz): output spins' magnetizations.

See also: [`freePrec`](@ref).
