```
get_bpf(; pass1 = 0.1, pass2 = 0.9, fs = 10.0, pole::Int = 4)
```

Create a Butterworth bandpass (or low-pass or high-pass) filter object. Set `pass1 = -1` for low-pass filter or `pass2 = -1` for high-pass filter.

**Arguments:**

  * `pass1`: (optional) first  passband frequency [Hz]
  * `pass2`: (optional) second passband frequency [Hz]
  * `fs`:    (optional) sampling frequency [Hz]
  * `pole`:  (optional) number of poles for Butterworth filter

**Returns:**

  * `bpf`: filter object
