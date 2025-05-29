```
doc_reaction(class::AbstractString)
```

Look up "class" using [`find_reaction`](@ref), and display fully-qualified Reaction Type and docstring in the Julia REPL.

NB: the VS Code Documentation browser has similar functionality and is often easier to use. The key difference that it looks at definitions *visible in the VS code projects and editor windows*, whilst `doc_reaction` looks at definitions *available to code in the current REPL* ie  provided by modules that are currently loaded in the REPL.
