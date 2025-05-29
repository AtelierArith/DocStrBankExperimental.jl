```
BasebandReplayChannel(filename; upsample=false, rxs=:, noise=nothing)
```

Load a baseband replay channel from a file.

If `upsample` is `true`, the impulse responses are upsampled to the delay axis sampling rate. This makes applying the channel faster but requires more memory. `rxs` controls which receivers to load from the file. By default, all receivers are loaded.

An additive noise model may be optionally specified as `noise`. If specified, it is used to corrupt the received signals.

Supported formats:

  * `.mat` (MATLAB) file in underwater acoustic channel repository (UACR) format. See https://github.com/uwa-channels/ for details.
