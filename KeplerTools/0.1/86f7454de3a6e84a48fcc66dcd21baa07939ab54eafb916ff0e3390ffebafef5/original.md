```
nextorb = propagate_across_soi(t, orb)
```

Searches for SoI changes starting at time `t`, and returns the orbit after the SoI patch if one occurs.

For periodic (elliptical) orbits, the search begins at time `t` and ends at a full period beyond time `t`. If no SoI change occurs, the original orbit is returned.

For hyperbolic orbits, the search begins at time `t` and ends at the time of SoI ejection. If the orbit's primary body has no SoI (i.e. it is a Star), the search ends at the time when the orbit is gauranteed to have passed beyond the outermost satellite of the star.
