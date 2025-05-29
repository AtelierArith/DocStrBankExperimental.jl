```
@vprintln(S::Symbol, k::Int, msg::String)
@vprintln S k msg

@vprintln(S::Symbol, msg::String)
@vprintln S msg
```

This macro can be used to control printings inside the code.

The macro `@vprintln` takes two or three arguments: a symbol `S` specifying a *verbosity scope*, an optional integer `k` and a string `msg`. If `k` is not specified, it is set by default to $1$.

To each verbosity scope `S` is associated a *verbosity level* `l` which is cached. If the verbosity level $l$ of `S` is bigger than or equal to $k$, the macro `@vprintln` triggers the printing of the associated string `msg` followed by a newline.

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

julia> function vprint_example()
       @vprintln :Test1 "Triggered"
       @vprintln :Test2 2 "Triggered"
       @vprintln :Test3 "Not triggered"
       @vprintln :Test2 4 "Not triggered"
       end
vprint_example (generic function with 1 method)

julia> vprint_example()
Triggered
Triggered
```

If one does not setup in advance a verbosity scope, the macro will raise an `ExceptionError` showing the error message "Not a valid symbol".
