```julia
add_dyn_injectors!(
    sys::PowerSystems.System,
    dyr_file::AbstractString
)

```

Add to a system already created the dynamic components. The system should already be parsed from a .raw file.

# Examples:

```julia
dyr_file = "Example.dyr"
add_dyn_injectors!(sys, dyr_file)
```
