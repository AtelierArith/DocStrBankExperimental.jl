```
scan_rundir(pth::String)
```

Scan a MITgcm run directory and standard output text file ("output.txt" or "STDOUT.0000") and return a NamedTuple of collected information (various formats)

Initially, the output looked like `(grid=gr,packages=pac,params_time=par1,params_grid=par2,completed=co)`
