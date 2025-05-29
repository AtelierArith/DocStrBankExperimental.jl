```
signal(x,[samplerate])
```

Coerce `x` to be a signal, optionally specifying its sample rate (usually in Hz). All signal operators first call `signal(x)` for each argument. This means you only need to call `signal` when you want to pass additional arguments to it.

!!! note
    If you pipe `signal` (e.g. `myobject |> signal(2kHz)`) you must specify the units of the sample rate, if passed. A unitless number is always interpreted as a constant, infinite-length signal (see below).


The types of objects that can be coerced to signals are as follows.
