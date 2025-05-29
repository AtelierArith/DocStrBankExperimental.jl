```
XPRS_MAXMEMORYSOFT
```

When RESOURCESTRATEGY is enabled, this control sets the maximum amount of memory in megabytes the optimizer targets to allocate. (integer)

This may change the solving path, but will not cause the solve to terminate early. To set a hard version of the same, please set MAXMEMORYHARD.

Default value: `0 (no limit)`

Domain: 0~+INF
