```
transitionwavelength(ion, transition::Tuple, chamber::Chamber; ignore_manualshift=false)
```

Returns The wavelength of the transition `transition` including the Zeeman shift experienced by `ion` given its position in `T`. `ion` may be either an Ion or an Int indicating the desired ion's index within `chamber`.
