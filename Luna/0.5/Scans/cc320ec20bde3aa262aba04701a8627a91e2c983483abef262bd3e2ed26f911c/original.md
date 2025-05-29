```
makefilename(scan, scanidx)
```

Make an appropriate file name for an `HDF5Output` or `prop_capillary` output for the `scan` at the current `scanidx`.

# Examples

```
scan = Scan("scan_example"; energy=collect(range(5e-6, 200e-6; length=64)))
runscan(scan) do scanidx, energyi
    prop_capillary(125e-6, 3, :He, 0.8; λ0=800e-9, τfwhm=10e-15, energy=energyi
                   filepath=makefilename(scan, scanidx))
end
```
