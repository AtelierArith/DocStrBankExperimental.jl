```
XPRS_MIPRESTART
```

Branch and Bound: controls strategy for in-tree restarts. (integer)

Default value: `-1`

Values: -1 : Determined automatically (`XPRS_MIPRESTART_DEFAULT`). 0 : Disable in-tree restarts (`XPRS_MIPRESTART_OFF`). 1 : Allow in-tree restarts at normal aggressiveness (`XPRS_MIPRESTART_MODERATE`). 2 : Allow in-tree restarts at higher aggressiveness (more likely to trigger a restart) (`XPRS_MIPRESTART_AGGRESSIVE`).
