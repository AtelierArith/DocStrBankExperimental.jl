```
XPRS_LPFLAGS
```

A bit-vector control which defines the algorithm for solving an LP problem or the initial LP relaxation of a MIP problem. (integer)

Default value: `0`

Values are a bitset: bit 0 : Use the dual simplex method. bit 1 : Use the primal simplex method. bit 2 : Use the barrier method (or hybrid gradient method if BARALG=4 is set). bit 3 : Use the network simplex method.
