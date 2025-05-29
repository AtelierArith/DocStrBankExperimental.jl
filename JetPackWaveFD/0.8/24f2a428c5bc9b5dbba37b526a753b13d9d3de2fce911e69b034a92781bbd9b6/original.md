```
srcillum(J)
srcillum(J, m)
srcillum!(y, J, m)
```

Compute and return the source illumination for `Jets` operator `J`. The source illumination  is defined as the sum of squares of the wavefield amplitudes everywhere in the model over  the time of the finite difference evolution. 

If `J::Jop` is a `Jets` block operator or distributed block operator, the source  illuminations from all blocks will be accumulated with a simple sum.

`srcillum(J)` creates and returns an array with the source illumination from `J::JopLn`,  using the current location defined in the `Jet`.

`srcillum(J, m)` creates and returns an array with the source illumination from `J::Jop`  for the location `m`.

`srcillum!(y, J, m)` zeros the passed array `y` and then accumulates to the source  illumination from `J::Jop` at the location `m` into `y`.
