```
time2freq(t)
```

converts time domain vector into a vector of frequencies according to the Nyquist criterion Port of Johanna Vannesjo's time2freq method: https://github.com/MRI-gradient/GIRF/blob/main/utils/time2freq.m

# Arguments

  * `t` - input time vector

# Outputs

  * `f` - Calculated requency axis, vector with [length(t)]
  * `df` - Frequency resolution
  * `f_max` - Full frequency range. The frequency axis range is [-f*max/2, f*max/2].
