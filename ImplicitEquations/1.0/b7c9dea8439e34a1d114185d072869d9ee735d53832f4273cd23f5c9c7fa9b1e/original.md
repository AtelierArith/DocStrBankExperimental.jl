Screen a value using `NaN` values. Use as  with `f(x,y) = x*y * screen(x > 0)`

Also aliased to `I_(x>0)`

An expression like `x::OInterval > 0` is not Boolean, but rather a `BInterval` which allows for a "MAYBE" state. As such, a simple ternary operator, like `x > 0 ? 1 : NaN` won't work, to screen values.
