Like LinearTicks but for multiples of `multiple`. Example where approximately 5 numbers should be found that are multiples of pi, printed like "1π", "2π", etc.:

```julia
MultiplesTicks(5, pi, "π")
```

If `strip_zero == true`, then the resulting labels will be checked and any label that is a multiple of 0 will be set to "0".
