```
XPRS_LOCALCHOICE
```

Controls when to perform a local backtrack between the two child nodes during a dive in the branch and bound tree. (integer)

Default value: `3`

Values: 1 : Never backtrack from the first child, unless it is dropped (infeasible or cut off). 2 : Always solve both child nodes before deciding which child to continue with. 3 : Automatically determined.
