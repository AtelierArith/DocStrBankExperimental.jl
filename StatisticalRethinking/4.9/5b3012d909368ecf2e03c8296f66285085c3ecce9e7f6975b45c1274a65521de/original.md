# sr_datadir

Relative path using the StatisticalRethinking src/ directory.

### Example to access `Howell1.csv` in StatisticalRethinking:

```julia
df = CSV.read(sr_datadir("Howell1.csv"), DataFrame)
```
