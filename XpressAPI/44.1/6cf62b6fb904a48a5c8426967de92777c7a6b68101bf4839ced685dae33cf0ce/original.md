```
XPRS_CUTDEPTH
```

Branch and Bound: Sets the maximum depth in the tree search at which cuts will be generated. (integer)

Generating cuts can take a lot of time, and is often less important at deeper levels of the tree since tighter bounds on the variables have already reduced the feasible region. A value of `0` signifies that no cuts will be generated.

Default value: `-1` determined automatically.

Domain: -1~+INF
