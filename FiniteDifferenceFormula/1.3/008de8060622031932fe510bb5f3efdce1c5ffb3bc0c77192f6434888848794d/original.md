`formula`()

Generate and list:

1. `k[1]*f(x[i+points[1]]) + k[2]*f(x[i+points[2]]) + ... + k[len]*f(x[i+points[len]])     = m*f^(n)(x[i]) + ..., m > 0`
2. The formula for f^(n)(x[i]), including estimation of accuracy in the big-O notation.
3. Julia function(s) for f^(n)(x[i]).

Calling `compute(n, points, true)` is the same as calling `compute(n, points)` and then `formula()`.

Even if no formula can be found, it still lists the computing results from which we can see why. For example, after `compute(2,1:2)`, try `formula()`.
