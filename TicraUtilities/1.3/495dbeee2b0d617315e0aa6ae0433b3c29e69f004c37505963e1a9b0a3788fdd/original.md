```
power(cut::Cut, θmax=180)
```

Compute the total radiated power in a Cut object.  If only a single phi value is included in the cut, then assume no azimuthal variation. The integration in the θ direction will be computed over the limits from 0 to `min(θmax, last(get_theta(cut)))`. `θmax` should be specified in degrees.
