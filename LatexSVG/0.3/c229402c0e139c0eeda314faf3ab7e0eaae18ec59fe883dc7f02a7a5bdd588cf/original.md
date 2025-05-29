```
texengine!(eng)
```

Sets the LaTeX engine for this session. `eng` can be [`PDFLaTeX`](@ref), [`XeLaTeX`](@ref), or [`LuaLaTeX`](@ref), e.g.

```julia
texengine!(PDFLaTeX)
```
