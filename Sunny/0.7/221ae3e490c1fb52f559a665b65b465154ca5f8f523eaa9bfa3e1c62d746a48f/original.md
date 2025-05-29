```
remove_periodicity!(sys::System, flags)
```

Remove periodic interactions along each dimension `d` if `flags[d]` is `true`. The system must support inhomogeneous interactions via [`to_inhomogeneous`](@ref).

# Example

```julia
# Remove periodic boundaries along the 1st and 3rd dimensions
remove_periodicity!(sys::System, (true, false, true))
```
