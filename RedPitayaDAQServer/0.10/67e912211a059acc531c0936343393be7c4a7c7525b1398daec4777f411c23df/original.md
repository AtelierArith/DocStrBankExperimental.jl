```
calibDACOffset!(rp::RedPitaya, channel::Integer, val)
```

Store calibration DAC offset `val` for given channel into the RedPitayas EEPROM.  This value is used by the server to offset the output voltage. Absolute value has to be smaller than 1.0 V. 
