```
check_allocs(func, types; ignore_throw=true)
```

Compiles the given function and types to LLVM IR and checks for allocations.

Returns a vector of `AllocationSite`, `DynamicDispatch`, and `AllocatingRuntimeCall`

!!! warning
    The Julia language/compiler does not guarantee that this result is stable across Julia invocations.

    If you rely on allocation-free code for safety/correctness, it is not sufficient to verify `check_allocs` in test code and expect that the corresponding call in production will not allocate at runtime.

    For this case, you must use `@check_allocs` instead.


# Example

```jldoctest
julia> function foo(x::Int, y::Int)
           z = x + y
           return z
       end
foo (generic function with 1 method)

julia> allocs = check_allocs(foo, (Int, Int))
AllocCheck.AllocationSite[]
```
