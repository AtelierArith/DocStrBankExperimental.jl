```
TranslationParityBasis(f, k, p, L; base=2, alloc=1000, threaded=true)
```

Construction for `TranslationParityBasis`.

## Inputs:

  * `f`       : Selection function for the basis contents.
  * `k`       : Momentum number, 0 or L/2.
  * `p`       : Parity number ±1.
  * `L`       : Length of the system.
  * `N`       : Particle numper.
  * `a`       : Length of unit cell.
  * `base`    : Base, default = 2.
  * `alloc`   : Size of the prealloc memory for the basis content, used only in multithreading, default = 1000.
  * `threaded`: Whether use the multithreading, default = true.

## Outputs:

  * `b`: TranslationParityBasis.
