`samplemethodargs(rng, mthd::Method)`

Samples arguments for method `mthd` using rng `rng`

```
f(x::Int, y::Real) = x + y
args = samplemethodargs(f)
f(args...)
```
