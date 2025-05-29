## Existing signals

Any existing signal just returns itself from `signal`. If a sample rate is specified it will be set if `x` has an unknown sample rate. If it has a known sample rate and doesn't match `samplerate(x)` an error will be thrown. If you want to change the sample rate of a signal use [`tosamplerate`](@ref).
