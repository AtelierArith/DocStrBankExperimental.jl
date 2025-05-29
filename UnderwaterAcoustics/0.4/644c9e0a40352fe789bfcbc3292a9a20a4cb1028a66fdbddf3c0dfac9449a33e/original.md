```
BasebandReplayChannel(h, θ, fs, fc, step=1; noise=nothing)
BasebandReplayChannel(h, fs, fc, step=1; noise=nothing)
```

Construct a baseband replay channel with impulse responses `h` and phase estimates `θ`. The phase estimates are optional. `fs` is the sampling frequency in Sa/s, `fc` is the carrier frequency in Hz, and `step` is the decimation rate for the time axis of `h`. The effective sampling frequency of the impulse responses is `fs ÷ step` impulse responses per second.

An additive noise model may be optionally specified as `noise`. If specified, it is used to corrupt the received signals.
