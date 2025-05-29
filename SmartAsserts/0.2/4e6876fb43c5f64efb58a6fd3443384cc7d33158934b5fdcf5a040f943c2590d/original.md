Like @assert, but try to also print out additional information about the arguments. Note that each argument is only evaluated once, so there is no extra overhead compared  to a normal assert.

Currently, additional information will be returned for the following types of expressions:

  * function calls: e.g., `a <= b`, `bool_f(a,k1=...; k2...)`
  * type asserts: e.g., `Type1 <: Type2`
  * comparison expressions: e.g., `a == b <= c + d <= e`

See also [`SmartAsserts.set_enabled`](@ref) on how to disable `@smart_assert`s  at compile-time.

## Examples

```julia
julia> let a = 1.0, rtol=0.1
           @smart_assert isapprox(a, sin(a), atol=0.05; rtol)
       end
ERROR: AssertionError: Condition `isapprox(a, sin(a), atol = 0.05; rtol)` failed due to:
        `a` evaluates to 1.0
        `sin(a)` evaluates to 0.8414709848078965
        `0.05` evaluates to 0.05
        `rtol` evaluates to 0.1
Stacktrace:
 ...
```
