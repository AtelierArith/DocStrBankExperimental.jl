```
rms_duration(m::S, r_ps::T, src::SourceParameters, sdof::Oscillator, rvt::RandomVibrationParameters) where {T<:Real}
```

Returns a 3-tuple of (Drms, Dex, Dratio), using a switch on `rvt.dur_rms`. Default `rvt` makes use of the `:BT14` model for excitation duration, `Dex`.

  * `m` is magnitude
  * `r_ps` is an equivalent point source distance
