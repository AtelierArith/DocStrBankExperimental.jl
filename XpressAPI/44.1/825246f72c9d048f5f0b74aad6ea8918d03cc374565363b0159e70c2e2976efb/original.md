```
XPRS_MIPABSGAPNOTIFYOBJ
```

Branch and bound: if the `gapnotify` callback has been set using XPRSaddcbgapnotify, then this callback will be triggered during the tree search when the best solution value reaches or passes the value you set of the `MIPRELGAPNOTIFYOBJ` control. (double)

Default value: `-1.0E+20` (for minimization problems); `1.0E+20` (for maximization problems)

Domain: [-1E+40,+1E+40]
