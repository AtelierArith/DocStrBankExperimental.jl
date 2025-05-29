```
MDMModel(sys; mu, md, mw, ma) -> sysm::MDMModel
```

Build for a vector of linear time-invariant system models `sys`, with the `i`-th component model `sys[i] = (Ai-λEi,Bi,Ci,Di)`, a multiple synthesis model object `sysm::MDMModel`  to be used in conjunction with the analysis and synthesis functions of model detection filters. 

The resulting multiple synthesis model object `sysm` contains the vector `sysm.sys`  of component models with partitioned inputs,  with the `i`-th model `sysm.sys[i] = (Ai-λEi,[Bui Bdi Bwi Bvi],Ci,[Dui Ddi Dwi Dvi])`, where  `Bui`, `Bdi`, `Bwi` and `Bvi` are formed from the successive columns of `Bi` and are  the input matrices from the control inputs `u`, disturbance inputs `di`,  noise inputs `wi` and auxiliary inputs `vi`, respectively,  and `Dui`, `Ddi`, `Dwi` and `Dvi` are formed from the successive columns of `Di` and  are the feedthrough matrices from those inputs. The dimensions of control, disturbance, noise and auxiliary input vectors are contained in  `sysm.mu`, `sysm.md[i]`, `sysm.mw[i]` and `sysm.ma[i]`, respectively.  

If `N` is the number of component models, the information on the partition of the input components  in control, disturbance, noise and auxiliary inputs can be specified using the following keyword arguments:

`mu = nu` specifies the dimension `nu` of control input vector `u` (default: `nu = 0`)

`md = nd` specifies the vector `nd` containing the `N` dimensions of disturbance input vectors, such that           the `i`-th disturbance vector `di` has dimension `nd[i]` (default: `nd = zeros(Int,N)`)

`mw = nw` specifies the vector `nw` containing the `N` dimensions of noise input vectors, such that           the `i`-th noise vector `wi` has dimension `nw[i]` (default: `nw = zeros(Int,N)`)

`ma = na` specifies the vector `na` containing the `N` dimensions of auxiliary input vectors, such that           the `i`-th auxiliary vector `vi` has dimension `na[i]` (default: `na = zeros(Int,N)`)
