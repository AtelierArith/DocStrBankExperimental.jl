```
filter(Din, dt_in; fmin=0, fmax=25)
```

Performs a causal filtering [fmin, fmax] on the input data bases on its sampling rate `dt`.  Automatically perfroms a lowpass if fmin=0 (default)
