```
@hassert(S::Symbol, k::Int, assert::Expr)
@hassert S k assert

@hassert(S::Symbol, assert::Expr)
@hassert S assert
```

This macro can be used to control assertion checks inside the code.

The macro `@hassert` takes two or three arguments: a symbol `S` specifying an *assertion scope*, an optional integer `k` and an assertion `assert`. If `k` is not specified, it is set by default to $1$.

To each assertion scope `S` is associated an *assertion level* `l` which is cached. If the assertion level $l$ of `S` is bigger than or equal to $k$, the macro `@hassert` triggers the check of the assertion `assert`. If `assert` is wrong, an `AssertionError` is thrown.

One can add a new assertion scope by calling the function [`add_assertion_scope`](@ref).

When starting a new instance, all the assertion levels are set to $0$. One can adjust the assertion level of an assertion scope by calling the function [`set_assertion_level`](@ref).

One can access the current assertion level of an assertion scope by calling the function [`get_assertion_level`](@ref).

# Examples

We will set up different assertion scopes with different assertion levels in a custom function to show how to use this macro.

```jldoctest
julia> AbstractAlgebra.add_assertion_scope(:MyScope)

julia> AbstractAlgebra.get_assertion_level(:MyScope)
0

julia> function hassert_test(x::Int)
       @hassert :MyScope 700 mod(x, 3) == 0
       return div(x, 3)
       end
hassert_test (generic function with 1 method)

julia> hassert_test(2)
0

julia> AbstractAlgebra.set_assertion_level(:MyScope, 701);

julia> try hassert_test(2)
       catch e e
       end
AssertionError("\$(Expr(:escape, :(mod(x, 3) == 0)))")

julia> hassert_test(3)
1

julia> AbstractAlgebra.set_assertion_level(:MyScope, 0)
0
```

If one does not setup in advance an assertion scope, the macro will raise an `ExceptionError` showing the error message "Not a valid symbol".
