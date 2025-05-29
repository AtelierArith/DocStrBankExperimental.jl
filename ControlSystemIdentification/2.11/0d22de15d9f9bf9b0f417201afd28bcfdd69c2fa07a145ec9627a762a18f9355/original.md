```
prefilter(d::AbstractIdData, l::Number, u::Number)
```

Filter input and output with a bandpass filter between `l` and `u` Hz. If `l = 0` a lowpass filter will be used, and if `u = Inf` a highpass filter will be used.
