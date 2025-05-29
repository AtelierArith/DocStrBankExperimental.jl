```
@v_do(S::Symbol, k::Int, act::Expr)
@v_do S k act

@v_do(S::Symbol, act::Expr)
@v_do S act
```

This macro can be used to control actions inside the code.

The macro `@v_do` takes two or three arguments: a symbol `S` specifying a *verbosity scope*, an optional integer `k` and an action `act`. If `k` is not specified, it is set by default to $1$.

To each verbosity scope `S` is associated a *verbosity level* `l`. If the verbosity level $l$ of `S` is bigger than or equal to $k$, the macro `@v_do` triggers the action `act`.

One can add a new verbosity scope by calling the function [`add_verbosity_scope`](@ref).

When starting a new instance, all the verbosity levels are set to $0$. One can adjust the verbosity level of a verbosity scope by calling the function [`set_verbosity_level`](@ref).

One can access the current verbosity level of a verbosity scope by calling the function [`get_verbosity_level`](@ref).

# Examples

We will set up different verbosity scopes with different verbosity levels in a custom function to show how to use this macro.

```jldoctest
julia> AbstractAlgebra.add_verbosity_scope(:Test1);

julia> AbstractAlgebra.add_verbosity_scope(:Test2);

julia> AbstractAlgebra.add_verbosity_scope(:Test3);

julia> AbstractAlgebra.set_verbosity_level(:Test1, 1);

julia> AbstractAlgebra.set_verbosity_level(:Test2, 3);

julia> function v_do_example(a::Int, b::Int, c::Int, d::Int)
       @v_do :Test1 a = 2*a
       @v_do :Test2 2 b = 3*b
       @v_do :Test3 c = 4*c
       @v_do :Test2 4 d = 5*d
       return (a, b, c, d)
       end
v_do_example (generic function with 1 method)

julia> v_do_example(1,1,1,1)
(2, 3, 1, 1)
```

If one does not setup in advance a verbosity scope, the macro will raise an `ExceptionError` showing the error message "Not a valid symbol".
