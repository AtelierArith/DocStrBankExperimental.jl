```
calibDACUpperLimit!(rp::RedPitaya, channel::Integer)
```

Store calibration DAC upper limit `val` for given channel into the RedPitayas EEPROM. This value is used by the server to limit the output voltage.
