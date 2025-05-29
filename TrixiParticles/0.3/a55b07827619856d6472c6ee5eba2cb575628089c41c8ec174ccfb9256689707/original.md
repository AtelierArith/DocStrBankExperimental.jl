```
validation_dir()
```

Return the directory where the validation files provided with TrixiParticles.jl are located. If TrixiParticles is installed as a regular package (with `]add TrixiParticles`), these files are read-only and should *not* be modified. To find out which files are available, use, e.g., `readdir`.

Copied from [Trixi.jl](https://github.com/trixi-framework/Trixi.jl).

# Examples

```@example
readdir(validation_dir())
```
