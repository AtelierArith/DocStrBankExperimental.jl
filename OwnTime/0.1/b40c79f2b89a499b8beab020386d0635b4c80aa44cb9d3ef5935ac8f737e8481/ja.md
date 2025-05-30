```
filecontains(needle)
```

与えられた `StackFrame` のファイルパスに `needle` が含まれている場合に `true` を返す `StackFrame` フィルターです。

# 例

```julia-repl
julia> stackframe = stacktrace()[1]
top-level scope at REPL[6]:1

julia> stackframe.file
Symbol("REPL[6]")

julia> filecontains("REPL")(stackframe)
true
```

関連情報: [`StackTraces.StackFrame`](@ref)
