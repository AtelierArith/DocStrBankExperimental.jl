```
nodeflux(system, F,U; data)
```

Reconstruction of an edge function as  vector function  on the nodes  of the triangulation.  The result  can be seen as a  piecewiesw linear vector function in the FEM space spanned by the discretization nodes exhibiting the flux density.

The reconstruction is based on the  "magic formula" R. Eymard, T. Gallouët, R. Herbin, IMA Journal of Numerical Analysis (2006) 26, 326−353, Lemma 2.4  (also: [hal.science/hal-00004840](https://hal.science/hal-00004840) ).

The return value is a `dim x nspec x nnodes` vector.

CAVEAT: there is a possible unsolved problem with the values at domain corners in the code. Please see any potential boundary artifacts as a manifestation of this issue and report them.
