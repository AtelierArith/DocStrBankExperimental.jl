```
XPRS_TUNERMODE
```

Tuner: Whether to always enable the tuner or disable it. (integer)

Default value: `-1`

Values: -1 : No effect. 0 : Always disable the tuner. `XPRStune` (`TUNE`) will have no effect. 1 : Always enable the tuner. `XPRSmipoptimize` (`MIPOPTIMIZE`), `XPRSlpoptimize` (`LPOPTIMIZE`), etc. will call the tuner before solving the problem.
