```
Sv(ping::EK60Ping;
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

Returns a `Vector` of Sv, the (Mean) Volume backscattering strength (MVBS) in (dB re 1 m-1) for a given `ping`.

The function accepts a number of optional arguments which, if specified, override the ping's own settings. This facilitates external calibration.
