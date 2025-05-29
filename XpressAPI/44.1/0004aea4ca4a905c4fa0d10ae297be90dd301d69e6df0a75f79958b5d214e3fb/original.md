```
XPRS_MIPKAPPAFREQ
```

Branch and Bound: Specifies how frequently the basis condition number (also known as kappa) should be calculated during the branch-and-bound search. (integer)

Default value: `0`

Values: 0 : Do not calculate condition numbers. 1 : Calculate conditions numbers on every node, including after each round of root cutting. n>1 : Calculate a condition number once per node of every n'th level of the branch-and-bound tree.
