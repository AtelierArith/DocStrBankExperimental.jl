```
examples_dir()
```

Return the directory where the example files provided with DispersiveShallowWater.jl are located. If DispersiveShallowWater is installed as a regular package (with `]add DispersiveShallowWater`), these files are read-only and should *not* be modified. To find out which files are available, use, e.g., `readdir`.

Copied from [Trixi.jl](https://github.com/trixi-framework/Trixi.jl).

# Examples

```@example
readdir(examples_dir())
```
