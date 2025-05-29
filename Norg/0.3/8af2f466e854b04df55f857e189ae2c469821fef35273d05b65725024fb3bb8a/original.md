Norg.jl provides a way to parse [Neorg](https://github.com/nvim-neorg/neorg) files in pure Julia.

It overloads `Base.parse` with custom targets. So far the only available target is `HTMLTarget`.

Example usage :

```julia
using Norg
norg(HTMLTarget(), "Read {https://github.com/nvim-neorg/norg-specs}[the spec !]")
```
