```
XPRS_BRANCHDISJ
```

Branch and Bound: Determines whether the optimizer should attempt to branch on general split disjunctions during the branch and bound search. (integer)

Default value: -1

Values: -1 : Automatic selection of the strategy. 0 : Disabled. 1 : Cautious strategy. Disjunctive branches will be created only for general integers with a wide range. 2 : Moderate strategy. 3 : Aggressive strategy. Disjunctive branches will be created for both binaries and integers.
