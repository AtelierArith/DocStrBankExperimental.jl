```
get_evec(c::Cut, ipol::Integer)
```

Return the ntheta × nphi matrix of complex numbers stored in polarization slot `ipol` of  the cut. `ipol` must be positive and less than or equal to `get_ncomp(cut)`.
