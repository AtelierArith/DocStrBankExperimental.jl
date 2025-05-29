```julia
compute_usings_imports(ex)::UsingsImports
```

Get the list of subexpressions like `using Module.Z, SomethingElse` or `import Module` that are contained in this expression.
