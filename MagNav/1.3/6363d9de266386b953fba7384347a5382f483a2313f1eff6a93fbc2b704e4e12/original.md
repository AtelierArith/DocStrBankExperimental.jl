```
eval_results(traj::Traj, ins::INS, filt_res::FILTres, crlb_P::Array)
```

Extract CRLB, INS, & filter results.

**Arguments:**

  * `traj`:     `Traj` trajectory struct
  * `ins`:      `INS` inertial navigation system struct
  * `filt_res`: `FILTres` filter results struct
  * `crlb_P`:   Cramér–Rao lower bound non-linear covariance matrix

**Returns:**

  * `crlb_out`: `CRLBout` Cramér–Rao lower bound extracted output struct
  * `ins_out`:  `INSout`  inertial navigation system extracted output struct
  * `filt_out`: `FILTout` filter extracted output struct
