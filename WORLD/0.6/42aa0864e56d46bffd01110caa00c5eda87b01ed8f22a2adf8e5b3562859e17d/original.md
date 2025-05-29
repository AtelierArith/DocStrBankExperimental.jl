```julia
mc2sp(mc, α, fftlen)

```

mc2sp converts mel-cepstrum to power spectrum envelope.

$c\_{\alpha}(m) -> |X(\omega)|^{2}$

equivalent: `exp(2real(MelGeneralizedCepstrums.mgc2sp(mc, α, 0.0, fftlen)))` Note that `MelGeneralizedCepstrums.mgc2sp` returns log magnitude spectrum.
