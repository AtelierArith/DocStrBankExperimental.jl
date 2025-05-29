```
vdi(v::VowelSpace; unstandardize=true)
```

Calculates the vowel dispersion index (vdi) for given `VowelSpace`, `v`. Effectively, it is a modification of the total variation of the vowel space density. Details are given in Kelley & Aalto (2019, Measuring the dispersion of density in head and neck cancer patients' vowel spaces: The vowel dispersion index, *Canadian Acoustics 47*(3), 114-115). Note that the vdi is a dimensionless number.

# Args

  * `v` The `VowelSpace` for which to calculate the vdi
  * `unstandardize` (keyword) Flag to convert the semi-normalized F1 and F2 in `v` to Hz (or whatever units were passed in when `v` was created).
