```
mp2rage_lookuptable(p::ParamsMP2RAGE;T1Range=1:0.5:10000,effInv = 0.96)

Compute lookup table according to the MP2RAGE parameters
```

# Arguments

  * `p::ParamsMP2RAGE`: MP2RAGE parameters structure

# Keywords

  * `T1Range` : T1 range computed
  * `effInv` : Inversion efficiency of the pulse

# Returns

  * lookUpTable (NaN .= 0)

# Bibliography

  * Marques JP, Kober T, Krueger G, van der Zwaag W, Van de Moortele P-F, Gruetter R. MP2RAGE, a self bias-field corrected sequence for improved segmentation and T1-mapping at high field. NeuroImage 2010;49:1271–1281 doi: 10.1016/j.neuroimage.2009.10.002.
