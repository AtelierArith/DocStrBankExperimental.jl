```
XPRS_MIPRESTARTGAPTHRESHOLD
```

Branch and Bound: Initial gap threshold to delay in-tree restart. (double)

The restart is delayed initially if the gap, given as a fraction between 0 and 1, is below this threshold. The optimizer adjusts the threshold every time a restart is delayed. Note that there are other criteria that can delay or prevent a restart.

Default value: `0.02`

Domain: [0.0, 1.0]
