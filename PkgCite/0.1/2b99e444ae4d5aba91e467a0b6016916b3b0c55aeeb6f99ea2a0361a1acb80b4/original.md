```
get_tool_citation(io::IO=stdout; jl = true, texttt = false, copy = true, cite_commands=Dict{String,String}(), filename="julia_citations.bib", badge=false)
```

Print a sentence describing the packages used in the current environment. If you only want to consider the direct dependencies, you can set `only_direct=true`. The sentence is automatically copied to the clipboard(you can avoid this by using `copy=false`). The package names have the .jl ending by default. You can ommit it with `jl=false`. Package names can be wrapped in `texttt` by setting `texttt=true` and you can also customize the cite command used for each package by using `cite_commands=Dict("PackageName"=>"custom_cite")`. The filename of the .bib file can be passed via the `filename` keyword. Use `badge = true` to get the citations from packages without a `Citation.bib` file, but with a DOI badge.
