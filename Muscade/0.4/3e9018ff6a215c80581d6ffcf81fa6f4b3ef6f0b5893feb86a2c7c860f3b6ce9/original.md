```
muscadeerror([[dbg,]msg])
```

Throw a `MuscadeException`, where

  * `dbg` is a `NamedTuple` that contains "location information"

(for example: solver, step, iteration, element, quadrature point) that will be displayed with the error message.

  * `msg` is a `String` describing the problem.
