```
FDIModel(sys; mu, md, mf, mw, ma) -> sysf::FDIModel
```

Build for a linear time-invariant descriptor system `sys = (A-λE,B,C,D)`  a synthesis model object `sysf::FDIModel`  to be used in conjunction with the analysis and synthesis functions of fault detection filters. 

The resulting synthesis model object `sysf` contains the component model with partitioned inputs,  `sysc.sys = (A-λE,[Bu Bd Bf Bw Bv],C,[Du Dd Df Dw Dv])`, where  `Bu`, `Bd`, `Bf`, `Bw` and `Bv` are formed from the successive columns of `B` and are  the input matrices from the control inputs `u`, disturbance inputs `d`, fault inputs `f`, noise inputs `w` and auxiliary inputs `v`, respectively,  and `Du`, `Dd`, `Df`, `Dw` and `Dv` are formed from the successive columns of `D` and  are the feedthrough matrices from those inputs. The dimensions of control, disturbance, fault, noise and auxiliary input vectors are contained in  `sysf.mu`, `sysf.md`, `sysf.mf`, `sysf.mw` and `sysf.ma`, respectively.  

The information on the partition of the input components  in control, disturbance, fault, noise and auxiliary inputs can be specified using the following keyword arguments:

`mu = nu` specifies the dimension `nu` of the control input vector `u` (default: `nu = 0`)

`md = nd` specifies the dimension `nd` of the disturbance input vector `d` (default: `nd = 0`)

`mf = nf` specifies the dimension `nf` of the fault input vector `f` (default: `nf = 0`)

`mw = nw` specifies the dimension `nw` of the noise input vector `w` (default: `nw = 0`)

`ma = na` specifies the dimension `na` of the auxiliary input vector `v` (default: `na = 0`)
