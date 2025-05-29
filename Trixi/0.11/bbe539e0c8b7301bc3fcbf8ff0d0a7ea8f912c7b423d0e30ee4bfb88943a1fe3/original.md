```
examples_dir()
```

Return the directory where the example files provided with Trixi.jl are located. If Trixi.jl is installed as a regular package (with `]add Trixi`), these files are read-only and should *not* be modified. To find out which files are available, use, e.g., `readdir`:

# Examples

```@example
readdir(examples_dir())
```
