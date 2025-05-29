```
FDFilterIF(sys; mu = 0, md = 0, mf = 0, mw = 0, ma = 0, moff = 0) -> R::FDFilterIF
```

Build for a given linear time-invariant descriptor system model `sys = (A-λE,B,C,D)`,  a fault detection filter internal form object `R`, as determined with the synthesis functions of FDI filters.  `mu`, `md`, `mf`, `mw` and `maux` are the dimensions of control, disturbance, fault, noise and auxiliary input vectors, respectively. It is assumed that `B = [Boff Bu Bd Bf Bw Bv]` and `D = [Doff Du Dd Df Dw Dv]` are partitioned matrices such that `Boff` and `Doff` have `moff` columns, `Bu` and `Du` have `mu` columns, `Bd` and `Dd` have `md` columns,  `Bf` and `Df` have `mf` columns,  `Bw` and `Dw` have `mw` columns, and `Bv` and `Dv` have `maux` columns.   

The resulting `R` contains the partitioned system  `R.sys = (A-λE,[Bu Bd Bf Bw Bv],C,[Du Dd Df Dw Dv])` and  the dimensions of control, disturbance, fault, noise and  auxiliary input vectors are contained in  `R.mu`, `R.md`, `R.mf`, `R.mw` and `R.ma`, respectively.  
