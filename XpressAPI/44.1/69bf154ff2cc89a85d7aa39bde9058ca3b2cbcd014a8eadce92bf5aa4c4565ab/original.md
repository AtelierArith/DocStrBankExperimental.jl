```
XPRS_REPAIRINFEASMAXTIME
```

**Deprecated**Overall time limit for the repairinfeas tool (integer)

Default value: `0`

Values: 0 : No time limit. n>0 : If an integer solution has been found, stop MIP search after n seconds, otherwise continue until an integer solution is finally found. n<0 : Stop in LP or MIP search after n seconds.
