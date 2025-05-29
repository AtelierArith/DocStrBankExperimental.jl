```
updateCarrierFreq!(pluto, value; doLog)
```

Changes the carrier frequency. Prints the new effective frequency.

# Arguments

  * `pluto::PlutoSDR` : the radio to modify.
  * `value::Int64` : the new carrier frequency.

# Keywords

  * `doLog::Bool` : toggles the display of the new carrier frequency

# Returns

  * `errno::Int` : 0 or a negative error code.
