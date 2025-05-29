```
spiral(a, b;
    action = :none,
    stepby = 0.01,
    period = 4pi,
    vertices = false,
    log =false)
spiral(a, b, action;
    stepby = 0.01,
    period = 4pi,
    vertices = false,
    log =false)
```

Make a spiral, and add it to the current path. The two primary parameters `a` and `b` determine the start radius, and the tightness.

For linear spirals (`log=false`), `b` values are:

  * lituus: -2
  * hyperbolic spiral: -1
  * Archimedes' spiral: 1
  * Fermat's spiral: 2

For logarithmic spirals (`log=true`):

  * golden spiral: b = ln(phi) / (pi/2) (about 0.30)

Values of `b` around 0.1 produce tighter, staircase-like spirals.
