```
gat(filename::AbstractString)
```

ハイライトテキスト これはGoで書かれた`gat`コマンドの薄いラッパーです。

`filename`がMarkdownの場合、`--render-markdown`オプションが追加されます。

# 例

```julia-repl
julia> using TerminalGat
julia> gat("README.md")
julia> gat("src/TerminalGat.jl")
```

ターミナルがSixelをサポートしている場合、ターミナルに画像を表示できます。

```julia-repl
julia> using TerminalGat
julia> using Plots; plot(sin); savefig("sin.png")
julia> gat("sin.png")
```
