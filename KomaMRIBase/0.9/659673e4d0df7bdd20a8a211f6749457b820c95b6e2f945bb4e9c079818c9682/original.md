```
rf = RF_fun(f::Function, T::Real, N::Int64)
```

Generate an RF sequence with amplitudes sampled from a function waveform.

!!! note
    This function is not being used in this KomaMRI version.


# Arguments

  * `f`: (`::Function`, [`T`]) function for the RF amplitud waveform
  * `T`: (`::Real`, [`s`]) duration of the RF pulse
  * `N`: (`::Int64`) number of samples of the RF pulse

# Returns

  * `rf`:(`::RF`) RF struct with amplitud defined by the function `f`
