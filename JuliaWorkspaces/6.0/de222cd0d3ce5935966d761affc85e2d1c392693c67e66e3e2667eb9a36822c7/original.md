```
get_julia_syntax_tree(jw::JuliaWorkspace, uri::URI)
```

Get the syntax tree of a Julia file from the workspace.

# Returns

  * The tuple `(tree, diagnostics)`, where `tree` is the syntax tree  and `diagnostics` is a vector of `Diagnostic` structs.
