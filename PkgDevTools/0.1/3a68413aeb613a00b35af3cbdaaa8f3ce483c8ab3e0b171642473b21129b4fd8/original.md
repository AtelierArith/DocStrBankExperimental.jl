```
synchronize_compats(code_dir::AbstractString)
```

This function

  * Recursively finds all Project.toml files in `code_dir`
  * Collects the compat entries
  * Finds any inconsistent compat entries
  * Asks the user (via `REPL.TerminalMenus`) which version (if any) to update to, and modifies the Project.toml files accordingly.
