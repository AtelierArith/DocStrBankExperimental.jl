```
sink([signal],[to=AxisArray];length,samplerate)
```

Creates a given type of object (`to`) from a signal. By default it is an `AxisArray` with time as the rows and channels as the columns. If a filename is specified for `to`, the signal is written to the given file. If given a type (e.g. `Array`) the signal is written to that type. The sample rate does not need to be specified, it will use either the sample rate of `signal` or a default sample rate (which raises a warning). 

You can specify a length or samplerate for the signal when calling sink if it has yet to be defined.
