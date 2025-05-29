```
transmit(ch::BasebandReplayChannel, x; rxs=:, abstime=false, noisy=true, fs=nothing, start=nothing)
```

Simulate the transmission of passband signal `x` through the channel model `ch`. If `txs` is specified, it specifies the indices of the sources active in the simulation. The number of sources must match the number of channels in the input signal. If `rxs` is specified, it specifies the indices of the receivers active in the simulation. Returns the received signal at the specified (or all) receivers.

`fs` specifies the sampling rate of the input signal. The output signal is sampled at the same rate. If `fs` is not specified but `x` is a `SampledSignal`, the sampling rate of `x` is used. Otherwise, the signal is assumed to be sampled at the channel's sampling rate.

If `abstime` is `true`, the returned signals begin at the start of transmission. Otherwise, the result is relative to the earliest arrival time of the signal at any receiver. If `noisy` is `true` and the channel has a noise model associated with it, the received signal is corrupted by additive noise.

If `start` is specified, it specifies the starting time index in the replay channel. If not specified, a random start time is chosen.
