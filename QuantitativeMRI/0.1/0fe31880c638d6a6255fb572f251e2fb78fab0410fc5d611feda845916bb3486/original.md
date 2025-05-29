```
mp2rage_lookuptable_radial(p::ParamsMP2RAGE;T1Range=1:0.5:10000,effInv = 0.96)

Compute lookup table according to the MP2RAGE parameters summing all the echoesl (mandatory for radial acquisition)
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
  * Faller TL, Trotier AJ, Miraux S, Ribot EJ. Radial MP2RAGE sequence for rapid 3D T1 mapping of mouse abdomen: application to hepatic metastases. Eur Radiol. 2019 Nov;29(11):5844-5851. doi: 10.1007/s00330-019-06081-3. Epub 2019 Mar 19. PMID: 30888483.
