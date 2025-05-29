```
XPRS_CUTFREQ
```

Branch and Bound: This specifies the frequency at which cuts are generated in the tree search. (integer)

If the depth of the node modulo `CUTFREQ` is zero, then cuts will be generated.

Default value: `-1` determined automatically.

Domain: -1~+INF
