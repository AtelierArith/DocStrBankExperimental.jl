```
mp2rage_comb(ima::Array{Complex{<:Real}})
mp2rage_comb(ima_magn::Array{<:Real},ima_phase::Array{<:Real})
```

Combine the image acquired at 2 differents inversion time (TI) in order to create a MP2RAGE image with the following equation. ima could be of any size but the last dimension needs to be the 2 TI.

If magnitude and phase image are passed to the function. It will combine them to create a complex image.

$\text{MP2RAGE} = Re(\frac{ima_{TI_1} \times conj(ima_{TI_2})}{|ima_{TI_1}|^2+|ima_{TI_2}|^2})$

# Arguments

  * `ima::Array{Complex{<:Real}}`: image of any dimension with TI = 2
  * `ima_magn::Array{<:Real},`: magnitude image of any dimension with TI = 2
  * `ima_phase::Array{<:Real},`: magnitude image of any dimension with TI = 2

# Keywords

# Returns

  * MP2RAGE images

# Bibliography

  * Marques JP, Kober T, Krueger G, van der Zwaag W, Van de Moortele P-F, Gruetter R. MP2RAGE, a self bias-field corrected sequence for improved segmentation and T1-mapping at high field. NeuroImage 2010;49:1271–1281 doi: 10.1016/j.neuroimage.2009.10.002.
