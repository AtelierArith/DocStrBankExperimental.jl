```
calibrationReport(E, Ecal, codata::Codata; unitIn="Hartree", msg=true)
```

Comparison of energy E with calibration value Ecal

default input: Hartree

#### Example:

```
julia> codata = castCodata(2022)
julia> calibrationReport(1.1, 1.0, codata; unitIn="Hartree")

calibration report (Float64):
Ecal = 1 Hartree
E = 1.1000000000000001 Hartree
absolute accuracy: ΔE = 0.1 Hartree (657.968 THz)
relative accuracy: ΔE/E = 0.0909091
```
