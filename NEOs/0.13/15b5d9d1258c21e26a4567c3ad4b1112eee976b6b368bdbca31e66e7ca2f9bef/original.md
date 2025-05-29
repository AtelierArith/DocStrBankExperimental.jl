```
absolutemagnitude(sol::NEOSolution{T, T}, params::NEOParameters{T}) where {T <: Real}
```

Return the absolute magnitude of orbit `sol`, as well as its standard error. This function uses the linear H and G model for asteroids.

!!! reference
    See https://minorplanetcenter.net/iau/ECS/MPCArchive/1985/MPC_19851227.pdf.

