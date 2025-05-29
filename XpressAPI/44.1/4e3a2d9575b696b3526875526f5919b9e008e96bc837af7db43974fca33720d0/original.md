```
XPRS_MIPPRESOLVE
```

Branch and Bound: Type of integer processing to be performed. (integer)

If set to `0`, no processing will be performed.

Default value: -1

Values are a bitset: bit 0 : Reduced cost fixing will be performed at each node. This can simplify the node before it is solved, by deducing that certain variables' values can be fixed based on additional bounds imposed on other variables at this node. bit 1 : Primal reductions will be performed at each node. Uses constraints of the node to tighten the range of variables, often resulting in fixing their values. This greatly simplifies the problem and may even determine optimality or infeasibility of the node before the simplex method commences. bit 2 : [Unused] This bit is no longer used to control probing. Refer to the integer control PREPROBING for setting probing level during presolve. bit 3 : If node preprocessing is allowed to change bounds on continuous columns. bit 4 : Dual reductions will be performed at each node. bit 5 : Allow global (non-bound) tightening of the problem during the tree search. bit 6 : The objective function will be used to find reductions at each node. bit 7 : [Unused] This bit is no longer used to control restarts. Refer to the integer control MIPRESTART for disabling tree restarts. bit 8 : Allow that symmetry is used to presolve the node problem.
