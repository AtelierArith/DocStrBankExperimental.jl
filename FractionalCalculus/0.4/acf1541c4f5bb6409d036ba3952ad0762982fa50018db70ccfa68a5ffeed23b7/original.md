# Caputo sense Piecewise algorithm

```
fracdiff(f, α, end_point, h, CaputoTrap())
```

Using piecewise linear interpolation function to approximate input function and combining Caputo derivative then implement summation.

### Example

```julia-repl
julia> fracdiff(x->x^5, 0.5, 2.5, 0.001, CaputoTrap())
```

Return the fractional derivative of $f(x)=x^5$ at point $x=2.5$.

```tex
@article{LI20113352,
title = {Numerical approaches to fractional calculus and fractional ordinary differential equation},
author = {Changpin Li and An Chen and Junjie Ye},
}
```
