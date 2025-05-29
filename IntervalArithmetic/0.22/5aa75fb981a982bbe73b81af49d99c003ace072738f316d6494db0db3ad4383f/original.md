```
IntervalArithmetic
```

Library for validated numerics using interval arithmetic, offering tools to rigorously bound errors in numerical computations by representing values as intervals and ensuring that computed results contain the true value. It provides accurate, and efficient methods, ideal for scientific computing, computer-assisted proofs, and any domain requiring certified numerical results.

Key features:

  * **Bound Type**: The default numerical type used to represent the bounds of the intervals. The default is `Float64`, but other subtypes of [`IntervalArithmetic.NumTypes`](@ref) can be used to adjust precision.
  * **Flavor**: The interval representation that adhere to the IEEE Standard 1788-2015. By default, it uses the set-based flavor, which excludes infinity to be part of an interval. Learn more: [`IntervalArithmetic.Flavor`](@ref).
  * **Interval Rounding**: Controls the rounding behavior for interval arithmetic operations. By default, the library employs correct rounding to ensure that bounds are computed as tightly as possible. Learn more: [`IntervalArithmetic.IntervalRounding`](@ref).
  * **Power mode**: A performance setting for power operations. The default mode uses an efficient algorithm prioritizing fast computation, but it can be adjusted for more precise, slower calculations if needed. Learn more: [`IntervalArithmetic.PowerMode`](@ref).
  * **Matrix Multiplication mode**: A performance setting for matrix multiplication operations. The default mode uses an efficient algorithm prioritizing fast computation, but it can be changed to use the standard definition of matrix multiplication. Learn more: [`IntervalArithmetic.MatMulMode`](@ref).

The default behaviors described above can be configured via [`IntervalArithmetic.configure`](@ref).

**Display Settings**: controls how intervals are displayed. By default, intervals are shown using the standard mathematical notation $[a, b]$, along with decorations and up to 6 significant digits. Learn more: [`setdisplay`](@ref).

# Usage

```julia
using IntervalArithmetic

# Create an interval
x = interval(1.0, 2.0)

# Perform a rigorous computation
x + exp(interval(π))
```

Learn more: https://github.com/JuliaIntervals/IntervalArithmetic.jl
