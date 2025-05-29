```
calibDACLowerLimit!(rp::RedPitaya, channel::Integer)
```

Store calibration DAC lower limit `val` for given channel into the RedPitayas EEPROM. This value is used by the server to limit the output voltage.
