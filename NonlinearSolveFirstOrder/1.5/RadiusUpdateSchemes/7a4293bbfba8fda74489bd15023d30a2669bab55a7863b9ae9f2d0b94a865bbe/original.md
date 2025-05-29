```
RadiusUpdateSchemes
```

`RadiusUpdateSchemes` is provides different types of radius update schemes implemented in the Trust Region method. These schemes specify how the radius of the so-called trust region is updated after each iteration of the algorithm. The specific role and caveats associated with each scheme are provided below.

## Using `RadiusUpdateSchemes`

Simply put the desired scheme as follows: `sol = solve(prob, alg = TrustRegion(radius_update_scheme = RadiusUpdateSchemes.Hei))`.
