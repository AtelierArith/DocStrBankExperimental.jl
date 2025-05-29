```
vcombine(α, x, β, y) -> dst
```

yields the linear combination `dst = α*x + β*y`.

---

To avoid allocating the result, the destination array `dst` can be specified with the in-place version of the method:

```
vcombine!(dst, α, x, β, y) -> dst
```

The code is optimized for some specific values of the multipliers `α` and `β`. For instance, if `α` (resp. `β`) is zero, then the prior contents of `x` (resp. `y`) is not used.

The source(s) and the destination can be the same.  For instance, the two following lines of code produce the same result:

```
vcombine!(dst, 1, dst, α, x)
vupdate!(dst, α, x)
```

See also: [`vscale!`](@ref), [`vupdate!](@ref).
