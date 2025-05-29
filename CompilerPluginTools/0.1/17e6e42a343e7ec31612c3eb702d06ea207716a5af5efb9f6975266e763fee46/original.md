```
const_invoke!(f, ir::IRCode, ref::GlobalRef)
```

Replace the function invoke `Expr(:invoke, _, ref, args...)` with `f(args...)` if its arguments `args` are all constant.
