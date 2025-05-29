```
fdimodset(sys; controls, c, disturbances, d, faults, f, fa, faults_sen, fs, noise, n, aux) -> sysf::FDIModel
```

Build for a given linear time-invariant system model `sys = (A-λE,B,C,D)`, a synthesis model object `sysf::FDIModel`  to be used in conjunction with the analysis and synthesis functions of FDI filters.  If `sys` is a vector of system models, then `sysf` results as a vector of synthesis model objects.

The information on the partition of the input components in control, disturbance, fault, noise and auxiliary inputs can be specified using the following keyword arguments:

`controls = inpu` or `c = inpu` specifies the indices `inpu` of the control inputs (default: void)

`disturbances = inpd` or `d = inpd` specifies the indices `inpd` of the disturbance inputs (default: void)

`faults = inpf` or `f  = inpf` specifies the indices `inpf` of the fault inputs (default: void)

`fa = inpfa` specifies the indices `inpfa` of control inputs subject to actuator fault (default: void)

`faults_sen = inpfs` or `fs = inpfs` specifies the indices `inpfs` of the system outputs subject to sensor fault inputs (default: void)

`noise = inpn` or  `noise = inpn` specifies the indices `inpn` of the noise inputs (default: void)

`aux = inpa` specifies the indices `inpa` of the auxiliary inputs (default: void)

The indices of inputs or outputs can be specified as integer vectors, integer scalars or integer `UnitRange`s.

The resulting `sysf` contains the partitioned system  `sysf.sys = (A-λE,[Bu Bd Bf Bw Bv],C,[Du Dd Df Dw Dv])`, where  `Bu`, `Bd`, `Bf`, `Bw` and `Bv` are the input matrices from the control inputs `u`, disturbance inputs `d`, fault inputs `f`,  noise inputs `w` and auxiliary inputs `v`, respectively, and `Du`, `Dd`, `Df`, `Dw` and `Dv` are the feedthrough matrices from those inputs. The dimensions of control, disturbance, fault, noise and auxiliary input vectors are contained in  `sysm.mu`, `sysm.md`, `sysm.mf`, `sysm.mw` and `sysm.ma`, respectively.  

*Method:* If `G(λ)` is the `p x m` transfer function matrix of `sys`, then the resulting system `sysf` has an  equivalent input output form `[Gu(λ) Gd(λ) Gf(λ) Gw(λ) Gv(λ)]`, where the following relations define the component matrices: `Gu(λ) = G(λ)*Su`, `Gd(λ) = G(λ)*Sd`,  `Gf(λ) = [G(λ)*Sf Ss]`, `Gw(λ) = G(λ)*Sw`,  `Gv(λ) = G(λ)*Sv`, with the selection matrices `Su`, `Sd`, `Sf`, `Sw` and `Sv` formed from the columns of the `m`-th order identity matrix and  `Ss` is formed  from the columns of the `p`-th order identity matrix. 
