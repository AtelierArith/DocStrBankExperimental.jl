```
@kcall [lib] cfunc(arg0::T0, arg1::T1, ...)::TR
```

Similar to `@ccall`. But it defines typeless arguments as pointers and typeless return values as `Cvoid`.
