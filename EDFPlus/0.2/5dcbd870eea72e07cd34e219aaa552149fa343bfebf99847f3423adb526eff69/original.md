```
mutable struct Annotation
```

These are text strings denoting a time, optionally duration, and a list of notes about the signal at that particular time in the recording. The first onset time of the annotation channel gives a fractional second offset adjustment of the start time of that record, which is specified in whole seconds in the header.
