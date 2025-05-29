```
FRD(w, r)
```

Represents frequency-response data. `w` holds the frequency vector and `r` the response. Methods defined on this type include

  * `+,-,*`
  * `length, vec, sqrt`
  * `plot`
  * `feedback`
  * [`freqvec`](@ref)
  * [`tfest`](@ref) to estimate a rational model
  * Indexing in the frequency domain using, e.g., `G[1Hz : 5Hz]`, `G[1rad : 5rad]`

If `r` represents a MIMO frequency response, the dimensions are `ny × nu × nω`.

An object `frd::FRD` can be plotted using `plot(frd, hz=false)` if `using Plots` has been called.
