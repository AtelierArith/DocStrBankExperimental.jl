```
format(x,fs,ch)
```

Efficiently convert both the samplerate (`fs`) and channels `ch` of signal `x`. This selects an optimal ordering for `tosamplerate` and `tochannels` to avoid redundant computations.
