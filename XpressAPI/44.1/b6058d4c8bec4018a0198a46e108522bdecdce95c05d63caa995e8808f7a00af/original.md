```
XPRS_GLOBALNUMINITNLPCUTS
```

Specifies the maximum number of tangent cuts when setting up the initial relaxation during a global solve. (integer)

By default, the algorithm chooses the number of cuts automatically. Adding more cuts tightens the problem, resulting in a smaller branch-and-bound tree, at the cost of slowing down each LP solve.

Default value: `-1` determined automatically.

Domain: -1,0~+INF
