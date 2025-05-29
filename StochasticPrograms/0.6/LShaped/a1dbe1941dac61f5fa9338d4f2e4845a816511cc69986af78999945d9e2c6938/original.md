```
SelectDecaying(T₀::Integer, T̲::Integer = 1, γ::T)
```

Behaves like [`SelectUniform`](@ref), but the uniform aggregate size decays by `γ` each iteration, starting from `T₀`. `T̲` is an optional lower bound on the aggregate size.
