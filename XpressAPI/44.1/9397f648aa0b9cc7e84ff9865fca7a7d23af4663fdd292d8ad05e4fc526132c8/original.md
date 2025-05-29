```
XPRS_PRECONEDECOMP
```

Presolve: decompose regular and rotated cones with more than two elements and apply Outer Approximation on the resulting components. (integer)

Default value: `-1`

Values: -1 : Automatically determined. 0 : Disable cone decomposition. 1 : Enable cone decomposition by replacing large cones with small ones in the presolved problem. 2 : Similar to 1, plus decomposition is enabled even if the cone variable is fixed. 3 : Cones are decomposed within the Outer Approximation domain only, i.e., the problem maintains the original cones.
