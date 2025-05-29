```
TranslationalBasis(f, k, L; base=2, alloc=1000, threaded=true)
```

Construction for `TranslationalBasis`.

## Inputs:

  * `dtype`   : Data type of index.
  * `L`       : Length of the system.
  * `f`       : Selection function for the basis contents.
  * `k`       : Momentum number from 0 to L-1.
  * `N`       : Particle number.
  * `a`       : Length of unit cell.
  * `base`    : Base, default = 2.
  * `alloc`   : Size of the prealloc memory for the basis content, used only in multithreading, default = 1000.
  * `threaded`: Whether use the multithreading, default = true.

## Outputs:

  * `b`: TranslationalBasis.
