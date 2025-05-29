```
LShapedAlgorithm
```

Functor object for the L-shaped algorithm.

...

# Algorithm parameters

  * `τ::AbstractFloat = 1e-6`: Relative tolerance for convergence checks.
  * `debug::Bool = false`: Specifies if extra information should be saved for debugging purposes. Defaults to false for memory efficiency.
  * `cut_scaling::AbstractFloat = 1.0`: Rescaling factor for cutting planes to improve numerical stability.
  * `log::Bool = true`: Specifices if L-shaped procedure should be logged on standard output or not.

...
