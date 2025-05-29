```
DefaultHandler(
    io::O,
    fmt::F=DefaultFormatter(),
    opts=Dict{Symbol, Any}();
    levels=nothing,
) where {F<:Formatter, O<:IO}
```

指定されたIOタイプでDefaultHandlerを作成します。

# 引数

  * `io::IO`: IOタイプ
  * `fmt::Formatter`: 使用するFormatter（デフォルトは`DefaultFormatter()`）
  * `opts::Dict`: オプション引数（デフォルトは`Dict{Symbol, Any}()`）
