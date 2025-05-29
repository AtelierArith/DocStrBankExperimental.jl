```
Sv(pings::Vector{EK60Ping};
    frequency=nothing,
    gain=nothing,
    equivalentbeamangle=nothing,
    soundvelocity=nothing,
    absorptioncoefficient=nothing,
    transmitpower=nothing,
    pulselength=nothing,
    sacorrection=nothing,
    rangecorrectionoffset=2)
```

Returns an `Array` of Sv, the Volume backscattering strength in (dB re 1 m-1) for a set of contiguous `pings`.

The function accepts a number of optional arguments which, if specified, override the pings' own settings. This facilitates external calibration.
