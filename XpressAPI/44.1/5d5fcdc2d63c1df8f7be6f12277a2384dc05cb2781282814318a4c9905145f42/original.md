```
XPRS_MAXMEMORYHARD
```

This control sets the maximum amount of memory in megabytes the optimizer should allocate. (integer)

If this limit is exceeded, the solve will terminate. This control is designed to make the optimizer stop in a controlled manner, so that the problem object is valid once termination occurs. The solve state will be set to incomplete. This is different to an out of memory condition in which case the optimizer returns an error. The optimizer may still allocate memory once the limit is exceeded to be able to finsish the operations and stop in a controlled manner. When RESOURCESTRATEGY is enabled, the control also has the same effect as MAXMEMORYSOFT and will cause the optimizer to try preserving memory when possible.

Default value: `0 (no limit)`

Domain: 0~+INF
