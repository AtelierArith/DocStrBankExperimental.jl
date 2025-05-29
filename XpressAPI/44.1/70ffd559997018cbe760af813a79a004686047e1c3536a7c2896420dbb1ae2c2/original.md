```
XPRS_NETSTALLLIMIT
```

Limit the number of degenerate pivots of the network simplex algorithm, before switching to either primal or dual simplex, depending on `ALGAFTERNETWORK`. (integer)

Default value: -1

Values: -1 : Automatically determined limit 0 : No limit. n>0 : Limit to n network simplex iterations.
