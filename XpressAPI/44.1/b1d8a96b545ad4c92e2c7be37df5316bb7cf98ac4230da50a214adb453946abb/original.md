```
XPRS_CUTSTRATEGY
```

Branch and Bound: This specifies the cut strategy. (integer)

A more aggressive cut strategy, generating a greater number of cuts, will result in fewer nodes to be explored, but with an associated time cost in generating the cuts. The fewer cuts generated, the less time taken, but the greater subsequent number of nodes to be explored.

Default value: `-1`

Values: -1 : Automatic selection of the cut strategy. 0 : No cuts. 1 : Conservative cut strategy. 2 : Moderate cut strategy. 3 : Aggressive cut strategy.
