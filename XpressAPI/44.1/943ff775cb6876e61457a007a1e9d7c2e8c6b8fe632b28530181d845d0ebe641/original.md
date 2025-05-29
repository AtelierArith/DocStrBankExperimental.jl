```
XPRS_RESOURCESTRATEGY
```

Controls whether the optimizer is allowed to make nondeterministic decisions if memory is running low in an effort to preserve memory and finish the solve. (integer)

Available memory (or container limits) are automatically detected but can also be changed by MAXMEMORYSOFT and MAXMEMORYHARD

Default value: `0`

Values: 1 : Allow the optimizer to change the solve path if necessary to preserve memory when getting close to one of the memory limits.
