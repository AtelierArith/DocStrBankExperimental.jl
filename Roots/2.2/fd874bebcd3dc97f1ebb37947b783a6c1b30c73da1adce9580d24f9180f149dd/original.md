```
FalsePosition([galadino_factor])
```

Use the [false position](https://en.wikipedia.org/wiki/False_position_method) method to find a zero for the function `f` within the bracketing interval `[a,b]`.

The false position method is a modified bisection method, where the midpoint between `[aₖ, bₖ]` is chosen to be the intersection point of the secant line with the $x$ axis, and not the average between the two values.

To speed up convergence for concave functions, this algorithm implements the $12$ reduction factors of Galdino (*A family of regula falsi root-finding methods*). These are specified by number, as in `FalsePosition(2)` or by one of three names `FalsePosition(:pegasus)`, `FalsePosition(:illinois)`, or `FalsePosition(:anderson_bjork)` (the default). The default choice has generally better performance than the others, though there are exceptions.

For some problems, the number of function calls can be greater than for the `Bisection` method, but generally this algorithm will make fewer function calls.

Examples

```
find_zero(x -> x^5 - x - 1, (-2, 2), FalsePosition())
```
