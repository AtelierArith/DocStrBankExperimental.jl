```
tfer = match_transfer_patch_positions(tfer; atol=1., maxit=100)
```

Attempts to optimize transfer start and end positions to ensure that patch times and positions are continuous on either side of a patch, and returns the optimized Transfer.
