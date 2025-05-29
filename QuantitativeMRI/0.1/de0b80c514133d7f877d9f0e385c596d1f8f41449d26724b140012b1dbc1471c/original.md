mp2rage*T1maps(im*MP2::Array{T},p::ParamsMP2RAGE;T1Range=1:10000,effInv = 0.96) where T <: Real

Compute Lookup table from MP2RAGE parameters.  keywords radial = false means that only the central echo is used to compute the signal (standard method for cartesian acquisition) If radial = true, all the echoes are sum.

# Arguments

  * `im_MP2::Array{T}`
  * `p::ParamsMP2RAGE`

# Keywords

  * T1Range = 1:10000
  * effInv = 0.96
  * radial = false

# Returns

  * T1map
  * T1Range
  * lookUpTable

# Bibliography

  * Marques JP, Kober T, Krueger G, van der Zwaag W, Van de Moortele P-F, Gruetter R. MP2RAGE, a self bias-field corrected sequence for improved segmentation and T1-mapping at high field. NeuroImage 2010;49:1271–1281 doi: 10.1016/j.neuroimage.2009.10.002.
