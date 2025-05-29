```
@breakpoint f(args...) condition=nothing
@breakpoint f(args...) line condition=nothing
```

Break upon entry, or at the specified line number, in the method called by `f(args...)`. Optionally supply a condition expressed in terms of the arguments and internal variables of the method. If `line` is supplied, it must be a literal integer.

# Example

Suppose a method `mysum` is defined as follows, where the numbers to the left are the line number in the file:

```
12 function mysum(A)
13     s = zero(eltype(A))
14     for a in A
15         s += a
16     end
17     return s
18 end
```

Then

```
@breakpoint mysum(A) 15 s>10
```

would cause execution of the loop to break whenever `s>10`.
