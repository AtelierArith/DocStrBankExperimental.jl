```
mcpc3ds_meepi(phase, mag; TEs, keyargs...)

mcpc3ds_meepi(compl; TEs, keyargs...)

mcpc3ds_meepi(phase; TEs, keyargs...)
```

Perform MCPC-3D-S phase offset removal on 5D MEEPI (multi-echo, multi-timepoint) input. The phase offsets are calculated for the template timepoint and removed from all volumes.

## Optional Keyword Arguments

  * `echoes`: only use the defined echoes. default: `echoes=[1,2]`
  * `sigma`: smoothing parameter for phase offsets. default: `sigma=[10,10,5]`
  * `po`: phase offsets are stored in this array. Can be used to retrieve phase offsets or work with memory mapping.
  * `template_tp`: timepoint for the template calculation. default: `template_tp=1`
