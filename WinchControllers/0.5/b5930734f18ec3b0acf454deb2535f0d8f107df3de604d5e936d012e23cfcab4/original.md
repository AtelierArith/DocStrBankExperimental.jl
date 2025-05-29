```
set_vset_pc(cvi::CalcVSetIn, v_set_pc, force)
```

## Parameters:

  * force:      measured tether force [N]
  * `v_set_pc`: only used during manual operation or park-at-length. If it is `nothing`,             `v_set_in` is calculated as function of the force.

## Returns:

  * nothing
