```
@check_allocs ignore_throw=true (function def)
```

Wraps the provided function definition so that all calls to it will be automatically checked for allocations.

If the check fails, an `AllocCheckFailure` exception is thrown containing the detailed failures, including the backtrace for each defect.

Note: All calls to the wrapped function are effectively a dynamic dispatch, which means they are type-unstable and may allocate memory at function *entry*. `@check_allocs` only guarantees the absence of allocations after the function has started running.

# Example

```jldoctest
julia> @check_allocs multiply(x,y) = x*y
multiply (generic function with 1 method)

julia> multiply(1.5, 3.5) # no allocations for Float64
5.25

julia> multiply(rand(3,3), rand(3,3)) # matmul needs to allocate the result
ERROR: @check_allocs function contains 1 allocations.

Stacktrace:
 [1] macro expansion
   @ ~/repos/AllocCheck/src/macro.jl:134 [inlined]
 [2] multiply(x::Matrix{Float64}, y::Matrix{Float64})
   @ Main ./REPL[2]:133
 [3] top-level scope
   @ REPL[5]:1
```
