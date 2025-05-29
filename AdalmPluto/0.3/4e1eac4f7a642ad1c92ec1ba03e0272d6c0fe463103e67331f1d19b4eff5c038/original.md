```
updateGainMode!(pluto[, mode])
```

Modifies the pluto RX channel gain control mode. Returns an error code < 0 if it doesn't succeed.

# Arguments

  * `pluto::PlutoSDR` : the radio to modify.
  * `mode::GainMode=DEFAULT` : the new gain mode. DEFAULT ≡ FAST_ATTACK.

# Returns

  * `errno::Int` : 0 or a negative error code.
