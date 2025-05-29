```
@unpack a, b, ... = x
```

Destructure properties `a`, `b`, ... of `x` into variables of the same name.

The behaviour of the macro is equivalent to `(; a, b, ...) = x` which was introduced in [Julia#39285](https://github.com/JuliaLang/julia/pull/39285) and is available in Julia >= 1.7.0-DEV.364.

See also [`@pack!`](@ref), [`@unpack_fields`](@ref), [`@pack_fields!`](@ref)
