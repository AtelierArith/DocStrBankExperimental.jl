```
all_evaluators(::Num)
all_evaluators(::Equation)
```

See `convex_evaluator`. This function performs the same task, but returns four functions (representing functions for the convex relaxation, concave relaxation, lower bound of the interval extension, and upper bound of the interval extension) [cv, cc, lo, hi] and the order vector.
