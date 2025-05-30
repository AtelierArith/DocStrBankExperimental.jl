`@showln x` prints "x = val", where `val` is the value of `x`, along with information about the function, file, and line number at which this statement was executed. For example:

```julia
function foo()
    x = 5
    @showln x
    x = 7
    @showln x
    nothing
end
```

might produce output like

```
x = 5
(in foo at ./error.jl:26 at /tmp/showln_test.jl:52)
x = 7
(in foo at ./error.jl:26 at /tmp/showln_test.jl:54)
```

If you need call depth information, see [`@showlnt`](@ref).
