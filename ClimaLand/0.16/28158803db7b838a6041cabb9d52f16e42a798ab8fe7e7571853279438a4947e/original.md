```
make_update_drivers(::AbstractClimaLandDrivers)
```

Creates and returns a function which updates the driver variables in the default case of no drivers. More generally, this should return a function which updates the driver fields stored in `p.drivers`.
