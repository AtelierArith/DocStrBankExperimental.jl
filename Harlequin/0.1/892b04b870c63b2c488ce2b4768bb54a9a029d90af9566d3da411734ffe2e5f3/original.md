```
update_scanning_strategy(sstr::ScanningStrategy)
```

Update the internal fields of a `ScanningStrategy` object. If you change any of the fields in a `ScanningStrategy` object after it has been created using the constructors, call this function before using one of the functions `time2pointing`, `time2pointing!`, `genpointings`, and `genpointings!`, as they rely on a number of internal parameters that need to be updated.

```julia
sstr = ScanningStrategy()
# ... use sstr ...

sstr.borespinang_rad *= 0.5
update_scanning_strategy(sstr)
```
