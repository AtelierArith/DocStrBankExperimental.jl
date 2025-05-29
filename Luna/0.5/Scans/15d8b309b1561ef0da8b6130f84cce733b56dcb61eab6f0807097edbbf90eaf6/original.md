```
runscan(f, scan)
```

Run the function `f` in a scan with arguments defined by the `scan::Scan`. The function `f` must have the signature `f(scanidx, args...)` where the length of `args` is the number of variables to be scanned over. Can be used with the `do` block syntax.

The exact subset and order of scan points which is run depends on `scan.exec`, see [`Scan`](@ref).

# Examples

```
scan = Scan("scan_example"; energy=collect(range(5e-6, 200e-6; length=64)))
runscan(scan) do scanidx, energyi
    prop_capillary(125e-6, 3, :He, 0.8; λ0=800e-9, τfwhm=10e-15, energy=energyi)
end
```
