```
cosine_ramp(x, dur_ramp, fs)
```

Applies raised-cosine ramp of dur `dur_ramp` (s) to input signal of sampling rate `fs` (Hz)

Applies a raised-cosine ramp to the input `x` with specified duration and sampling rate. Note that this ramp is the square of a cosine ramp, or equivalently the Hann function:     1/2 * [1 - cos(2πn/N)], 0 ≤ n ≤ N evaluated from 0 to N where N is twice the length of the ramp in samples:
