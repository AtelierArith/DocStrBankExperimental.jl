```
Rg_to_PPFD(Rg,J_to_mol=4.6,frac_PAR=0.5)
PPFD_to_Rg(PPFD,J_to_mol=4.6,frac_PAR=0.5)
```

Conversions between Global Radiation (W m-2) and Photosynthetic Photon Flux  Density (umol m-2 s-1)

# Arguments

  * Rg:       Global radiation = incoming short-wave radiation at the surface (W m-2)
  * PPFD:     Photosynthetic photon flux density (umol m-2 s-1)
  * J*to*mol: Conversion factor from J m-2 s-1 (= W m-2) to umol (quanta) m-2 s-1
  * frac_PAR: Fraction of incoming solar irradiance that is photosynthetical-           active radiation (PAR); defaults to 0.5

# Details

The conversion is given by:

$PPFD = Rg * frac_PAR * J_to_mol$

by default, the combined conversion factor (`frac_PAR * J_to_mol`) is 2.3

# Examples

```@example
# convert a measured incoming short-wave radiation of 500 Wm-2 to
# PPFD in umol m-2 s-1 and backwards
Rg_to_PPFD(500)
PPFD_to_Rg(1150)
```
