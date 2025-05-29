```
FDIFilter(sys, ny, mu) -> Q::FDIFilter
```

Build for a vector of linear time-invariant descriptor system models `sys[i] = (Ai-λEi,Bi,Ci,Di)` with the same number of inputs, a fault detection and isolation filter object `Q`,  as determined with the synthesis functions of FDI filters.  `ny` and `mu` are the number of measured outputs and the number of control inputs, respectively.  It is assumed that each `Bi = [Byi Bui Bvi]` and `Di = [Dyi Dui Dvi]` are partitioned matrices such that `Byi` and `Dyi` have `ny` columns, and `Bui` and `Dui` have `mu` columns,  where `Byi` and `Bui` are the input matrices from the measured outputs `y` and  control inputs `u`, `Dyi` and `Dui` are the feedthrough matrices from the measured outputs `y` and  control inputs `u`. 

The resulting `Q` contains the vector of partitioned systems `Q.sys[i] = (Ai-λEi,[Byi Bdi],Ci,[Dyi Dui])` and the dimensions of the  partitioned filter input vectors as  `measured outputs` and `control inputs`,   can be accessed as the integers contained in `Q.ny` and `Q.mu`, respectively. 
