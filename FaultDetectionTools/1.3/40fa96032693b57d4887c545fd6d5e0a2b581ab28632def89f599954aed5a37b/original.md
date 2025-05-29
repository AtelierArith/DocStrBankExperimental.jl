```
FDFilter(sys, ny, mu) -> Q::FDFilter
```

Build for a given linear time-invariant descriptor system model `sys = (A-λE,B,C,D)`,  a fault detection filter object `Q`, as determined with the synthesis functions of FDI filters.  `ny` and `mu` are the number of measured outputs and the number of control inputs, respectively.  It is assumed that `B = [By Bu Bv]` and `D = [Dy Du Dv]` are partitioned matrices such that `By` and `Dy` have `ny` columns, and `Bu` and `Du` have `mu` columns,  where `By` and `Bu` are the input matrices from the measured outputs `y` and  control inputs `u`, `Dy` and `Du` are the feedthrough matrices from the measured outputs `y` and  control inputs `u`. 

The resulting `Q` contains the partitioned system  `Q.sys = (A-λE,[By Bd],C,[Dy Du])` and the dimensions of the  partitioned filter input vectors as  `measured outputs` and `control inputs`,   can be accessed as the integers contained in `Q.ny` and `Q.mu`, respectively. 
