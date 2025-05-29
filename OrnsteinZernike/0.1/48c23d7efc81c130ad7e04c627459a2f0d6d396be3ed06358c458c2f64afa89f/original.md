```
OZSolution
```

Holds the solution of an Ornstein Zernike problem. 

Fields:

  * r: vector of distances
  * k: vector of wave numbers
  * gr: radial distribution function
  * Sk: static structure factor
  * ck: direct correlation function in k space
  * cr: direct correlation function in real space

if the system was a single-component system, `gr`, `Sk`, `ck` and `cr` are vectors.  If instead the system was a multicomponent one, they are three dimensional vectors,  where the first dimension contains the values along r, and the second and third dimension contain the data for the species.
