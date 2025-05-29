```
XPRS_HISTORYCOSTS
```

Branch and Bound: How to update the pseudo cost for a MIP entity when a strong branch or a regular branch is applied. (integer)

Default value: `-1`

Values: -1 : Automatically determined. 0 : No update. 1 : Update using only regular branches from the root to the current node. 2 : Same as 1, but update with strong branching results as well. 3 : Update using any regular branching or strong branching information from all nodes solves before the current node.
