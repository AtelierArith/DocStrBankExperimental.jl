```
XPRS_BACKTRACKTIE
```

Branch and Bound: Specifies how to break ties when selecting the next node to work on when a full backtrack is performed. (integer)

The options are the same as for the BACKTRACK control.

Default value: `-1`

Values: -1 : Default selection. 1 : Unused. 2 : Select the node with the best estimated solution. 3 : Select the node with the best bound on the solution. 4 : Select the deepest node in the search tree (equivalent to depth-first search). 5 : Select the highest node in the search tree (equivalent to breadth-first search). 6 : Select the earliest node created. 7 : Select the latest node created. 8 : Select a node randomly. 9 : Select the node whose LP relaxation contains the fewest number of infeasible MIP entities. 10 : Combination of 2 and 9. 11 : Combination of 2 and 4. 12 : Combination of 3 and 4.
