```
quadosc(fn, a, Inf, fnzeros; ...)
```

Integrate the function `fn(x)` from `a` to `Inf`. The function `fnzeros(n)` takes an integer `n` and is such that `fn(fnzeros(n)) == 0`. The algorithm works by integrating between successive zeros, and accelerating the alternating series.

The argument `pren` is the number of intervals to integrate before applying the series acceleration.

`atol` and `rtol` specify the absolute and relative tolerances for determining convergence.

`order` is passed on to `quadgk()` of the [QuadGK](https://github.com/JuliaMath/QuadGK.jl) package.

`nconvergences` is the number of iterations before convergence is declared.

See `?QuadOsc.accel_cohen_villegas_zagier` for details on the series acceleration.
