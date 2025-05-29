```
XPRS_MIPCOMPONENTS
```

Determines whether disconnected components in a MIP should be solved as separate MIPs. (integer)

There can be significant performence benefits from solving disconnected components individual instead of being part of the main branch-and-bound search.

Default value: `-1`

Values: -1 : Automatic - let the solver decide. 0 : Disable solving disconnected components separately. 1 : Solve disconnected components separately.
