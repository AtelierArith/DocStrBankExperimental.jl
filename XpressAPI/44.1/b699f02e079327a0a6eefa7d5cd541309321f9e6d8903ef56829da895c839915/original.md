```
XPRS_COVERCUTS
```

Branch and Bound: The number of rounds of lifted cover inequalities at the top node. (integer)

A lifted cover inequality is an additional constraint that can be particularly effective at reducing the size of the feasible region without removing potential integral solutions. The process of generating these can be carried out a number of times, further reducing the feasible region, albeit incurring a time penalty. There is usually a good payoff from generating these at the top node, since these inequalities then apply to every subsequent node in the tree search.

Default value: `-1` determined automatically.

Domain: -1~+INF
