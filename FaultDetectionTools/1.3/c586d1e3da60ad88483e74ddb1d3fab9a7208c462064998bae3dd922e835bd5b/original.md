```
FDIFilterIF(sys; mu = 0, md = 0, mf = 0, mw = 0, ma = 0, moff = 0 ) -> R::FDIFilterIF
```

Build for a vector of linear time-invariant descriptor system models `sys[i] = (Ai-λEi,Bi,Ci,Di)`,  a fault detection and isolation filter internal form object `R`, as determined with the synthesis functions of FDI filters.  `mu`, `md`, `mf`, `mw` and `ma` are the dimensions of control, disturbance, fault, noise and auxiliary input vectors, respectively. It is assumed that each `Bi = [Boffi Bui Bdi Bfi Bwi Bvi]` and `Di = [Doffi Dui Ddi Dfi Dwi Dvi]` are partitioned matrices such that `Boffi` and `Doffi` have `moff` columns, `Bui` and `Dui` have `mu` columns, `Bdi` and `Ddi` have `md` columns,  `Bfi` and `Dfi` have `mf` columns,  `Bwi` and `Dwi` have `mw` columns, and `Bvi` and `Dvi` have `ma` columns.   

The resulting `R` contains the vector of partitioned systems  `R.sys[i] = (A-λE,[Bui Bdi Bfi Bwi Bvi],C,[Dui Ddi Dfi Dwi Dvi])` and  the dimensions of control, disturbance, fault, noise and auxiliary input vectors are contained in  `R.mu`, `R.md`, `R.mf`, `R.mw` and `R.ma`, respectively.  
