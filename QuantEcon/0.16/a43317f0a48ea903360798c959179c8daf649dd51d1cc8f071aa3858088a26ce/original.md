Given a function `f` and an initial guessed range `x1` to `x2`, the routine expands the range geometrically until a root is bracketed by the returned values `x1` and `x2` (in which case zbrac returns true) or until the range becomes unacceptably large (in which case a `ConvergenceError` is thrown).

##### Arguments

  * `f::Function`: The function you want to bracket
  * `x1::T`: Initial guess for lower border of bracket
  * `x2::T`: Initial guess ofr upper border of bracket
  * `;ntry::Int(50)`: The maximum number of expansion iterations
  * `;fac::Float64(1.6)`: Expansion factor (higher ⟶ larger interval size jumps)

##### Returns

  * `x1::T`: The lower end of an actual bracketing interval
  * `x2::T`: The upper end of an actual bracketing interval

##### References

This method is `zbrac` from numerical recipies in C++

##### Exceptions

  * Throws a `ConvergenceError` if the maximum number of iterations is exceeded
