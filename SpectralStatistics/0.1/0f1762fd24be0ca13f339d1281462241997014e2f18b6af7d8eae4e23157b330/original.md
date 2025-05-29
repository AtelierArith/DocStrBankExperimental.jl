```
unfold_spectrum(spect::DataSample, f::Function) → unfolded::UnfoldedSpectrum
```

Return the unfolded spectrum of `spect` by using the function `f`  as the smooth part of the integrated density of states.

## Arguments

  * `spect`: Spectrum to be unfolded.
  * `f(x)` : Function modeling the smooth part of the integrated density of states, where the argument `x` is the energy.

## Returns

  * `unfolded` : The unfolded spectrum as an instance of type [`UnfoldedSpectrum`](@ref).
