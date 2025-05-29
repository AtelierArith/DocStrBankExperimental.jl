```
AcousticSource(pos, frequency; spl=0)
AcousticSource(x, z, frequency; spl=0)
AcousticSource(x, y, z, frequency; spl=0)
```

An source at location `pos` with nominal `frequency` and source level `spl` (dB re 1 µPa @ 1 m). The source is assumed to be omnidirectional and well approximated by a point source. While the source may have some bandwidth, the nominal frequency is used to estimate propagation effects such as absorption, reflection coefficients, etc.

If the location of the source is unknown, it may be specified as `nothing`. This is useful when the propagation model does not require the source location (e.g., data-driven models).
