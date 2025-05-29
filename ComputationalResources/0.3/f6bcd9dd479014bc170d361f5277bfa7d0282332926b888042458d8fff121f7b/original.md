```
ArrayFireLibs()
ArrayFireLibs(settings)
```

Indicate that computation should be performing using the ArrayFire libraries. Optionally pass in an object specifying algorithmic settings.

# Examples:

```julia
filter(ArrayFireLibs(), image, kernel)
filter(ArrayFireLibs(backend), image, kernel)
```
