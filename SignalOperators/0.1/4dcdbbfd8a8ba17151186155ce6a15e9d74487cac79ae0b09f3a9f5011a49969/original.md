## Functions

```
signal(fn,[samplerate];[ω/frequency],[ϕ/phase])
```

Functions can define infinite length signals of known or unknown sample rate. The function `fn` can either return a number, or, for multi-channel signals, a tuple of values. 

The input to `fn` is either a phase value or a time value. If passed a frequency (using either the ω or frequency keyword), the input to `fn` will be a phase value in radians, ranging from 0 to 2π. If no frequency is specified the value passed to `fn` is the time in seconds. Specifying phase (by the ϕ or phase keyword) will first add that value to the input before passing it to `fn`. The phase is assumed to be in units of radians (but you can also pass degrees by using `°` or a unit of time (e.g. `s` for seconds)).
