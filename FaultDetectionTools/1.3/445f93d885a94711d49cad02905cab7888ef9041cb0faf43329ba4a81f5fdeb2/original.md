```
mdmodset(sys; controls, c, disturbances, d, noise, n, aux) -> sysm::MDMModel
```

Build for a vector of linear time-invariant system models `sys`, with the `i`-th component model  `sys[i] = (Ai-λEi,Bi,Ci,Di)`, a multiple synthesis model object `sysm::MDMModel`  to be used in conjunction with the analysis and synthesis functions of model detection filters. 

The information on the partition of the input components in control, disturbance, noise and auxiliary inputs can be specified using the following keyword arguments:

`controls = inpu` or `c = inpu` specifies the indices `inpu` of the control inputs (default: void)

`disturbances = inpd` or `d = inpd` specifies the indices or a vector of indices `inpd` of the disturbance inputs (default: void)

`noise = inpn` or  `noise = inpn` specifies the indices or a vector of indices `inpn` of the noise inputs (default: void)

`aux = inpa` specifies the indices or a vector of indices `inpa` of the auxiliary inputs (default: void)

The indices of inputs can be specified as integer vectors, integer scalars or integer `UnitRange`s. For disturbance, noise and auxiliary inputs, vectors of integer vectors or  vectors of integer `UnitRange`s can be used to specify possibly different set of indices for each component model.

The resulting `sysm` contains the vector `sysm.sys` of partitioned systems, with the `i`-th model   `sysm.sys[i] = (Ai-λEi,[Bui Bdi Bwi Bvi],Ci,[Dui Ddi Dwi Dvi])`, where  `Bui`, `Bdi`, `Bwi` and `Bvi` are the input matrices from the control inputs `u`, disturbance inputs `di`,  noise inputs `wi` and auxiliary inputs `vi`, respectively, and `Dui`, `Ddi`, `Dwi` and `Dvi` are the feedthrough matrices from those inputs. The dimensions of control, disturbance, noise and auxiliary input vectors are contained in  `sysm.mu`, `sysm.md[i]`, `sysm.mw[i]` and `sysm.ma[i]`, respectively.  

*Method:* If `Gi(λ)` is the `p x mi` transfer function matrix of `sys[i]`, then the resulting component system `sysm.sys[i]` has an  equivalent input output form `[Gui(λ) Gdi(λ) Gwi(λ) Gvi(λ)]`, where the following relations define the component matrices: `Gui(λ) = Gi(λ)*Su`, `Gdi(λ) = Gi(λ)*Sdi`,  `Gwi(λ) = G(λ)*Swi`,  `Gvi(λ) = Gi(λ)*Svi`, with the selection matrices `Su`, `Sdi`, `Swi` and `Svi` formed from the columns of the `mi`-th order identity matrix  (note that `Su` is the same for all component models). 
