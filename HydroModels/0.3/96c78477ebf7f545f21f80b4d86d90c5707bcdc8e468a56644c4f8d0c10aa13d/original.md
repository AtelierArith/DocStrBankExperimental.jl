```
ManualSolver{mutable} <: AbstractHydroSolver
```

A lightweight, type-stable ODE solver optimized for hydrological modeling.

# Type Parameters

  * `mutable::Bool`: Controls array mutability and performance characteristics

      * `true`: Uses mutable arrays for in-place updates (30% faster)
      * `false`: Uses immutable arrays for functional programming style

# Description

ManualSolver implements a fixed-step explicit Euler method for solving ordinary  differential equations (ODEs). It is specifically designed for hydrological models  where stability and computational efficiency are prioritized over high-order accuracy.

## Performance Characteristics

  * Type-stable implementation for predictable performance
  * Optional in-place operations via the `mutable` parameter
  * Linear time complexity with respect to simulation length
  * Constant space complexity when `mutable=true`

## Memory Management

  * `mutable=true`: 

      * Modifies arrays in-place
  * `mutable=false`:

      * Creates new arrays at each step
