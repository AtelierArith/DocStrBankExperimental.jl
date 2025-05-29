```
ishermitian(T::ITensor; kwargs...)
```

Test whether an ITensor is a Hermitian operator, that is whether taking `dag` of the ITensor and transposing its indices returns numerically the same ITensor.
