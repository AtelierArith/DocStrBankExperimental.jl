```
XPRS_BRANCHCHOICE
```

Once a MIP entity has been selected for branching, this control determines which of the branches is solved first. (integer)

Default value: `0`

Values: 0 : Minimum estimate branch first. 1 : Maximum estimate branch first. 2 : If an incumbent solution exists, solve the branch satisfied by that solution first. Otherwise solve the minimum estimate branch first (option 0). 3 : Solve first the branch that forces the value of the branching variable to move farther away from the value it had at the root node. If the branching entity is not a simple variable, solve the minimum estimate branch first (option 0).
