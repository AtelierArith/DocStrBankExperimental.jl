```
sink!(array,x;[samplerate],[offset])
```

Write `size(array,1)` samples of signal `x` to `array`, starting from the sample after `offset`. If no sample rate has been specified for `x` you can specify it now, using `samplerate` (it will default to 44.1kHz).
