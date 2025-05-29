```
MDModel(sys; mu, md, mw, ma) -> sysc::MDModel
```

Build for a linear time-invariant descriptor system `sys = (A-λE,B,C,D)`  a component synthesis model object `sysm::MDModel`  to be used in conjunction with the analysis and synthesis functions of model detection filters. 

The resulting synthesis model object `sysc` contains the component model with partitioned inputs,  `sysc.sys = (A-λE,[Bu Bd Bw Bv],C,[Du Dd Dw Dv])`, where  `Bu`, `Bd`, `Bw` and `Bv` are formed from the successive columns of `B` and are  the input matrices from the control inputs `u`, disturbance inputs `d`,  noise inputs `w` and auxiliary inputs `v`, respectively,  and `Du`, `Dd`, `Dw` and `Dv` are formed from the successive columns of `D` and  are the feedthrough matrices from those inputs. The dimensions of control, disturbance, noise and auxiliary input vectors are contained in  `sysm.mu`, `sysm.md`, `sysm.mw` and `sysm.ma`, respectively.  

The information on the partition of the input components  in control, disturbance, noise and auxiliary inputs can be specified using the following keyword arguments:

`mu = nu` specifies the dimension `nu` of the control input vector `u` (default: `nu = 0`)

`md = nd` specifies the dimension `nd` of the disturbance input vector `d` (default: `nd = 0`)

`mw = nw` specifies the dimension `nw` of the noise input vector `w` (default: `nw = 0`)

`ma = na` specifies the dimension `na` of the auxiliary input vector `v` (default: `na = 0`)
