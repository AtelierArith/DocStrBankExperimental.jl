```
DefaultHandler(
    filename::AbstractString,
    fmt::F=DefaultFormatter(),
    opts=Dict{Symbol, Any}();
    levels=nothing,
) where {F<:Formatter}
```

指定されたファイル名へのIOハンドルを持つDefaultHandlerを作成します。

# 引数

  * `filename::AbstractString`: 書き込むログファイルのファイル名
  * `fmt::Formatter`: 使用するFormatter（デフォルトは`DefaultFormatter()`）
  * `opts::Dict`: オプション引数（デフォルトは`Dict{Symbol, Any}()`）
