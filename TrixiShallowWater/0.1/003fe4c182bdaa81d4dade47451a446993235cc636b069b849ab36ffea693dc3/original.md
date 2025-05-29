```
min_max_speed_chen_noelle(u_ll, u_rr, orientation::Integer,
                          equations::ShallowWaterEquations1D)
```

The approximated speeds for the HLL type numerical flux used by Chen and Noelle for their hydrostatic reconstruction. As they state in the paper, these speeds are chosen for the numerical flux to ensure positivity and to satisfy an entropy inequality.

Further details on this hydrostatic reconstruction and its motivation can be found in

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
