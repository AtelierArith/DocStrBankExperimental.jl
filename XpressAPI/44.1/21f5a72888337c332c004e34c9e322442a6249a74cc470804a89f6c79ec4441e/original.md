```
XPRS_MIPFRACREDUCE
```

Branch and Bound: Specifies how often the optimizer should run a heuristic to reduce the number of fractional integer variables in the node LP solutions. (integer)

Default value: `-1`

Values: -1 : Automatic. 0 : Disabled. 1 : Run before and after cutting on the root node. 2 : Run also during root cutting. 3 : Run also during the tree search.
