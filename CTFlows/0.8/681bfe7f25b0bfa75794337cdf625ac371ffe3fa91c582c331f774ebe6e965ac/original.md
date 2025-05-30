Macros for Lie and Poisson brackets

# Example

```@example
julia> F0 = VectorField(x -> [x[1], x[2], (1-x[3])])
julia> F1 = VectorField(x -> [0, -x[3], x[2]])
julia> @Lie [F0, F1]([1, 2, 3])
[0, 5, 4]
#
julia> F0 = VectorField((t, x) -> [t+x[1], x[2], (1-x[3])], autonomous=false)
julia> F1 = VectorField((t, x) -> [t, -x[3], x[2]], autonomous=false)
julia> @Lie [F0, F1](1, [1, 2, 3])
#
julia> F0 = VectorField((x, v) -> [x[1]+v, x[2], (1-x[3])], variable=true)
julia> F1 = VectorField((x, v) -> [0, -x[3]-v, x[2]], variable=true)
julia> @Lie [F0, F1]([1, 2, 3], 2)
#
julia> F0 = VectorField((t, x, v) -> [t+x[1]+v, x[2], (1-x[3])], autonomous=false, variable=true)
julia> F1 = VectorField((t, x, v) -> [t, -x[3]-v, x[2]], autonomous=false, variable=true)
julia> @Lie [F0, F1](1, [1, 2, 3], 2)
#
julia> H0 = Hamiltonian((x, p) -> 0.5*(2x[1]^2+x[2]^2+p[1]^2))
julia> H1 = Hamiltonian((x, p) -> 0.5*(3x[1]^2+x[2]^2+p[2]^2))
julia> @Lie {H0, H1}([1, 2, 3], [1, 0, 7])
3.0
#
julia> H0 = Hamiltonian((t, x, p) -> 0.5*(x[1]^2+x[2]^2+p[1]^2), autonomous=false)
julia> H1 = Hamiltonian((t, x, p) -> 0.5*(x[1]^2+x[2]^2+p[2]^2), autonomous=false)
julia> @Lie {H0, H1}(1, [1, 2, 3], [1, 0, 7])
#
julia> H0 = Hamiltonian((x, p, v) -> 0.5*(x[1]^2+x[2]^2+p[1]^2+v), variable=true)
julia> H1 = Hamiltonian((x, p, v) -> 0.5*(x[1]^2+x[2]^2+p[2]^2+v), variable=true)
julia> @Lie {H0, H1}([1, 2, 3], [1, 0, 7], 2)
#
julia> H0 = Hamiltonian((t, x, p, v) -> 0.5*(x[1]^2+x[2]^2+p[1]^2+v), autonomous=false, variable=true)
julia> H1 = Hamiltonian((t, x, p, v) -> 0.5*(x[1]^2+x[2]^2+p[2]^2+v), autonomous=false, variable=true)
julia> @Lie {H0, H1}(1, [1, 2, 3], [1, 0, 7], 2)
#
```
