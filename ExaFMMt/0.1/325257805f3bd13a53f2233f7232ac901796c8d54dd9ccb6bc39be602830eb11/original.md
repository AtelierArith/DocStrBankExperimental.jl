```
HelmholtzFMMOptions{I, C} <: FMMOptions
```

Helmoltz-initializer for setup function.  

# Fields

  * `p::I`: Multipole expansion order.
  * `ncrit::I`: Minimum number of points in each box of the tree.
  * `wavek::C`: Wavenumber.
