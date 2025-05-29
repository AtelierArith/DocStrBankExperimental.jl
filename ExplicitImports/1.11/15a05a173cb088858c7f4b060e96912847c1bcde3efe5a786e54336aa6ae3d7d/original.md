```
print_explicit_imports_script([io::IO=stdout,] path; skip=(Base, Core), warn_improper_explicit_imports=true)
```

Analyzes the script located at `path` and prints information about reliance on implicit exports as well as any "improper" explicit imports (if `warn_improper_explicit_imports=true`).

Note that the particular printing may change in future non-breaking releases of ExplicitImports.

!!! warning
    The script (or at least, all imports in the script) must be run before this function can give reliable results, since it relies on introspecting what names are present in `Main`.


## Keyword arguments

  * `skip=(mod, Base, Core)`: any names coming from the listed modules (or any submodules thereof) will be skipped. Since `mod` is included by default, implicit imports of names exported from its own submodules will not count by default.
