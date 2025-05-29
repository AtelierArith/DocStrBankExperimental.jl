```
@spectra [expr=BlockSpectralMatrix]
```

Unpack a block vector. This is equivalent to calling `getblock` for all the  sub-blocks and putting them in a Tuple. 

# Example

```julia
# compute stacked EE,BB mode-coupling matrix from mask alm
M_EE_BB = mcm(:EE_BB, map2alm(mask1), map2alm(mask2))
# apply the 2×2 block mode-coupling matrix to the stacked EE and BB spectra
@spectra Cl_EE, Cl_BB = M_EE_BB \ [pCl_EE; pCl_BB]
```
