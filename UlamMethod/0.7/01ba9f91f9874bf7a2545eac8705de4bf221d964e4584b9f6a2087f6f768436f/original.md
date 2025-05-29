```
viz!(object; kwargs...)
```

This function wraps `Meshes.viz!` for `UlamMethod` objects for plotting.

### Methods

```
viz!(boundary; kwargs...)
```

Plot a boundary.

```
viz!(bins; kwargs...)
```

Plot the bins.

```
viz!(binner; kwargs...)
```

Plot `binner.bins`.

```
viz!(data; kwargs...)
```

Plot a `2 x N` matrix of points.

---

### The docstring for `Meshes.viz!` is provided below.

---

```
viz!(object; [options])
```

Visualize Meshes.jl `object` in an existing scene with `options` forwarded to [`viz`](@ref).
