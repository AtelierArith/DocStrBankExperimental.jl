```
XPRS_FEASIBILITYJUMP
```

MIP: Decides if the Feasibility Jump heuristic should be run. (integer)

The value for this control is either -1 (let Xpress decide), 0 (off) or a value that indicates for which type of models the heuristic should be run.

Default value: `-1`

Values: -1 : Use automatic settings. 0 : Turned off. 1 : Run the heuristic on models with all integer variables. 2 : Run the heuristic on models in which all non-integer variables have bounds [0,1]. 3 : Run the heuristic on models in which all non-integer variables have integer bounds.
