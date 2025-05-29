```
tfer = match_transfer_patch_times(startorb, endorb, stime, etime, patch_posns; atol=1e-6, maxit=100)
tfer = match_transfer_patch_times(tfer; kwargs...)
```

Attempts to optimize transfer start and end times to ensure that patch times are continuous on either side of a patch, and returns the optimized Transfer.
