```
gat(filename::AbstractString)
```

Hightlight text This is a thin wrapper for `gat` command written in Go.

if `filename` is a Markdown, the `--render-markdown` option is added.

# Example

```julia-repl
julia> using TerminalGat
julia> gat("README.md")
julia> gat("src/TerminalGat.jl")
```

If your terminal supports Sixel, you can display images in your terminal

```julia-repl
julia> using TerminalGat
julia> using Plots; plot(sin); savefig("sin.png")
julia> gat("sin.png")
```
