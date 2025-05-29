```
updateBandwidth!(pluto, value)
```

Changes the bandwidth. Prints the new value.

# Arguments

  * `pluto::PlutoSDR` : the radio to modify.
  * `value::Int64` : the new sampling rate.

# Keywords

  * `doLog::Bool` : toggles the display of the new carrier frequency

# Returns

  * `errno::Int` : 0 or a negative error code.
