```
@vprint(S::Symbol, k::Int, msg::String)
@vprint S k msg

@vprint(S::Symbol, msg::String)
@vprint S msg
```

The same as [`@vprintln`](@ref), but without the final newline.
