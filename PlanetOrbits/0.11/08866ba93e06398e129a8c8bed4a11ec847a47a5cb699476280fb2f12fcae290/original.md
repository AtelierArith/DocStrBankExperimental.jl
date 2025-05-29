```
AbsoluteVisual{OrbitType}(..., ref_epoch=, ra=, dec=, plx=, rv=, pmra=, pmdec=)
```

This wraps another orbit object to add parallax, proper motion, and RV fields, at a given reference epoch. 

Like a Visual{OrbitType} this allows for calculating projected quantities, eg. separation in milliarcseconds.

What this type additionally does is correct for the star's 3D motion through space (RV and proper motion) and differential light travel-time compared to a reference epoch when calculating various quantities.  This becomes necessary when computing eg. RVs over a long time period.

ra        : degrees dec       : degrees parallax  : mas pmra      : mas/yr pmdec     : mas/yr rv        : m/s ref_epoch : years

TODO: account for viewing angle differences and differential light travel time between a planet and its host.
