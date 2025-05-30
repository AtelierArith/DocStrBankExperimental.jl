`@showlnt x` prints "x = val", where `val` is the value of `x`, along with information about the function, file, and line number at which this statement was executed, using indentation to indicate recursion depth. For example:

```julia
function recurses(n)
    @showlnt n
    n += 1
    @showlnt n
    if n < 10
        n = recurses(n)
    end
    return n
end
```

might produce output like

```
        x = 5
        (in foo at ./error.jl:26 at /tmp/showln_test.jl:52)
        x = 7
        (in foo at ./error.jl:26 at /tmp/showln_test.jl:54)
```

This macro causes a backtrace to be taken, and looking up the corresponding code information is relatively expensive, so using `@showlnt` can have a substantial performance cost.

The indentation of the line is proportional to the length of the backtrace, and consequently is an indication of recursion depth.
