```
@ismatch value pattern
```

Return `true` if `value` matches `pattern`, `false` otherwise.  When returning `true`, binds the pattern variables in the enclosing scope.

See also `@match` for the syntax of patterns

# Examples

```julia-repl
julia> struct Point
            x
            y
        end

julia> p = Point(0, 3)
Point(0, 3)

julia> if @ismatch p Point(0, y)
            println("On the y axis at y = ", y)
        end
On the y axis at y = 3
```

Guarded patterns ought not be used with `@ismatch`, as you can just use `&&` instead:

```julia-repl
julia> if (@ismatch p Point(x, y)) && x < y
            println("The point (", x, ", ", y, ") is in the upper left semiplane")
        end
The point (0, 3) is in the upper left semiplane
```
