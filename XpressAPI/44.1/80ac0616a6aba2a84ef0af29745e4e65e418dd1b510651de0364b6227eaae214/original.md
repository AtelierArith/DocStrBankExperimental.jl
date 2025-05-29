```
XPRS_HEURSEARCHROOTCUTFREQ
```

How frequently to run the local search heuristic during root cutting. (integer)

This is given as how many cut rounds to perform between runs of the heuristic. Set to zero to avoid applying the heuristic during root cutting. Branch and Bound: This specifies how often the local search heuristic should be run in the tree.

Default value: `-1`

Values: -1 : Automatic. 0 : Disabled heuristic during cutting. n>0 : Number of cutting rounds between each run.
