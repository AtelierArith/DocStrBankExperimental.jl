```
B = rfgr2B(rf, gr, loc=[0 0 0]u"cm"; Δf=0u"Hz", b1Map=1, γ=γ¹H)
```

Turn rf, `rf`, and gradient, `gr`, into 𝐵-effective magnetic field.

*INPUTS*:

  * `rf::TypeND(RF0D, [1,2])` (nT, (nCoil))
  * `gr::TypeND(GR0D, [2])`   (nT, 3)
  * `loc::TypeND(L0D, [2])`   (1,3) or (nM, 3), locations.

*KEYWORDS*:

  * `Δf::TypeND(F0D, [0,1,2])` (1,)  or (nM,), off-resonance.
  * `b1Map::TypeND(Union{Real,Complex},[0,1,2])` (1,) or (nM,(nCoils)),  transmit sensitivity.
  * `γ::TypeND(Γ0D, [0,1])` (1,)  or (nM,), gyro-ratio

*OUTPUS*:

  * `B`, generator of `TypeND(B0D, [2])` (1,1,nT), 𝐵 field.

See also: [`Pulse2B`](@ref), [`blochSim`](@ref).

# TODO:

Support `loc`, `Δf`, and `b1Map` being `Base.Generators`.
