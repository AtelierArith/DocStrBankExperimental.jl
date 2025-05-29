```
MatsubaraFreq(n)
```

Prefactor `n` of the Matsubara frequency `ω = n*π/β`

Struct representing the Matsubara frequency ω entering the Fourier transform of a propagator G(τ) on imaginary time τ to its Matsubara equivalent Ĝ(iω) on the imaginary-frequency axis:

```
        β
Ĝ(iω) = ∫  dτ exp(iωτ) G(τ)      with    ω = n π/β,
        0
```

where β is inverse temperature and by convention we include the imaginary unit in the frequency argument, i.e, Ĝ(iω). The frequencies depend on the statistics of the propagator, i.e., we have that:

```
G(τ - β) = ± G(τ)
```

where + is for bosons and - is for fermions. The frequencies are restricted accordingly.

  * Bosonic frequency (`S == Fermionic`): `n` even (periodic in β)
  * Fermionic frequency (`S == Bosonic`): `n` odd (anti-periodic in β)
