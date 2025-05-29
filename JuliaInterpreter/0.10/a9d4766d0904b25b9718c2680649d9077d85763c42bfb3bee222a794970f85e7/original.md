```
breakpoint(f, [sig], [line], [condition])
```

Add a breakpoint to `f` with the specified argument types `sig`.¨ If `sig` is not given, the breakpoint will apply to all methods of `f`. If `f` is a method, the breakpoint will only apply to that method. Optionally specify an absolute line number `line` in the source file; the default is to break upon entry at the first line of the body. Without `condition`, the breakpoint will be triggered every time it is encountered; the second only if `condition` evaluates to `true`. `condition` should be written in terms of the arguments and local variables of `f`.

# Example

```julia
function radius2(x, y)
    return x^2 + y^2
end

breakpoint(radius2, Tuple{Int,Int}, :(y > x))
```
