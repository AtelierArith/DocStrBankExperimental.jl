```
transmissionloss(pm::PropagationModel, tx1::AcousticSource, rx1::AcousticReceiver; mode=:coherent)
transmissionloss(pm::PropagationModel, tx1::AcousticSource, rx::AbstractArray{<:AcousticReceiver}; mode=:coherent)
```

Compute the transmission loss in dB from `tx1` to `rx1` or all receivers in `rx`. The mode may be `:coherent` or `:incoherent`.
