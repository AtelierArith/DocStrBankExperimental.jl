```
updateGain!(pluto, value)
```

Changes the gain control mode to manual et sets the given value. Prints a warning and returns the error code if it doesn't succeed.

# Arguments

  * `pluto::PlutoSDR` : the radio to modify.
  * `value::Int64` : the manual gain value.

# Returns

  * `errno::Int` : 0 or a negative error code.
