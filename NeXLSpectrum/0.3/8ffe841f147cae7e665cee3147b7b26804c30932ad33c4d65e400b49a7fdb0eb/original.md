```
multiscore(specs::AbstractArray{<:Spectrum}, e0=specs[1][:BeamEnergy])
```

Compares each spectrum against the mean spectrum by comparing the 200 eV to 500 eV range with the [e0/2,e0/1.5] range. If all spectra are equivalent at low energies then all the scores will be close to zero.  A number less than zero means that the low energy region of the spectrum was depressed relative to the others.  A number more than zero means that the high energy region of the spectrum was elevated relative to the others.  The multi-score is sensitive to tilt and obstructions like surface texture which may make one spectrum's low energy be more absorbed than the  others. 
