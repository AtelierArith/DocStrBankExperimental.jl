```
eval_crlb(traj::Traj, crlb_P::Array)
```

Extract Cramér–Rao lower bound (CRLB) results.

**Arguments:**

  * `traj`:   `Traj` trajectory struct
  * `crlb_P`: Cramér–Rao lower bound non-linear covariance matrix

**Returns:**

  * `crlb_out`: `CRLBout` Cramér–Rao lower bound extracted output struct
