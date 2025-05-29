```
fftdims(p::Plan)
```

Return an iterable of the dimensions that are transformed by the FFT plan `p`.

# Implementation

For legacy reasons, the default definition of `fftdims` returns `p.region`. Hence this method should be implemented only for `Plan` subtypes that do not store the transformed dimensions in a field named `region`.
