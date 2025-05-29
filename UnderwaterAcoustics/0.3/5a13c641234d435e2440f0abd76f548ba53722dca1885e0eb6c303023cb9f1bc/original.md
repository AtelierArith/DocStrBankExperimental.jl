```
transfercoef(pm::PropagationModel, tx1::AcousticSource, rx1::AcousticReceiver; mode=:coherent)
transfercoef(pm::PropagationModel, tx1::AcousticSource, rx::AbstractArray{<:AcousticReceiver}; mode=:coherent)
```

Compute the complex transfer coefficients from `tx1` to `rx1` or all receivers in `rx`. The mode may be `:coherent` or `:incoherent`.
