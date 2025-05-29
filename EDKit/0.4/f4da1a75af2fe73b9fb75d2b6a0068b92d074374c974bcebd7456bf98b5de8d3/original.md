TranslationFlipBasis(f, k, p, L; base=2, alloc=1000, threaded=true)

Construction for `TranslationFlipBasis`.

## Inputs:

  * `f`       : Selection function for the basis contents.
  * `k`       : Momentum number from 0 to L-1.
  * `p`       : Parity number (under spin flip) ±1.
  * `L`       : Length of the system.
  * `base`    : Base, default = 2.
  * `alloc`   : Size of the prealloc memory for the basis content, used only in multithreading, default = 1000.
  * `threaded`: Whether use the multithreading, default = true.

## Outputs:

  * `b`: TranslationFlipBasis.
