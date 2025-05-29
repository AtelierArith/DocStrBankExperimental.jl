```
@vprint(S::Symbol, k::Int, msg::String)
@vprint S k msg

@vprint(S::Symbol, msg::String)
@vprint S msg
```

[`@vprintln`](@ref) と同じですが、最後の改行がありません。
