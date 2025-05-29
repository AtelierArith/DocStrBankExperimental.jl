```
recalibrate(s::Spectrum{T}, es::LinearEnergyScale)
```

Allows changing the energy scale on a spectrum from one LinearEnergyScale to another as though the spectrum were  measured on a different detector.  The algorith uses a FFT-base scheme to rescale and shift the spectral data. Ths scheme allows for fractional shifts of offset and fractional changes in the width.  It is limited in that the change in width must produce an integral number of channels in the resulting spectrum.  The algorithm  maintains the total spectrum integral so the new spectrum can be used for quantitative purposes. Plotting one spectrum over the other should maintain peak position but is likely to change the channel counts.
