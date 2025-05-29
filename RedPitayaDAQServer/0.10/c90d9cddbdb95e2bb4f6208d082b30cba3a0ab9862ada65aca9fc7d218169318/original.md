```
calibADCOffset!(rp::RedPitaya, channel::Integer, val)
```

Store calibration ADC offset `val` for given channel into the RedPitayas EEPROM. Absolute value has to be smaller than 1.0 V.

See also [convertSamplesToPeriods!](@ref),[convertSamplesToFrames](@ref).
