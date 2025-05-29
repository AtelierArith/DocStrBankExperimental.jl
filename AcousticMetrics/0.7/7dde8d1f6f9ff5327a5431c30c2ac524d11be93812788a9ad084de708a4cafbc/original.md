```
PressureTimeHistory(sm::AbstractNarrowbandSpectrum, p=similar(halfcomplex(sm)))
```

Construct a pressure time history from a narrowband spectrum `sm`.

The optional `p` argument will be used to store the pressure vector of the pressure time history, and should have length `inputlength(sm)`.
