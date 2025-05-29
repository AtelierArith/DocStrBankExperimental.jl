```
XPRS_IFCHECKCONVEXITY
```

Determines if the convexity of the problem is checked before optimization. (integer)

Applies to quadratic, mixed integer quadratic and quadratically constrained problems. Checking convexity takes some time, thus for problems that are known to be convex it might be reasonable to switch the checking off.

Default value: `1`

Values: 0 : Turn off convexity checking. 1 : Turn on convexity checking.
