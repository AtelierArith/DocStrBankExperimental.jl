```
TrussNode(position::Vector{Float64}, dofs::Vector{Bool}, id::Symbol = nothing)
```

Instantiate a 3 DOF node with given position and fixities. Optional symbol identifier, `id`.

# Example

```julia-repl
julia> TrussNode([1., 1., 56.], [false, true, true])
TrussNode([1.0, 1.0, 56.0], Bool[0, 1, 1], #undef, [0.0, 0.0, 0.0, 0.0, 0.0, 0.0], [0.0, 0.0, 0.0, 0.0, 0.0, 0.0], nothing)
```

---

```
TrussNode(position::Vector{Float64}, fixity::Symbol, id::Symbol = nothing)
```

Instantiate a 3 DOF node with given position and common boundary type. Optional symbol identifier, `id`.

Available boundary conditions:

  * :free
  * :pinned
  * :(x/y/z)free
  * :(x/y/z)fixed

# Example

```julia-repl
julia> TrussNode([1., 1., 56.], :pinned)
TrussNode([1.0, 1.0, 56.0], Bool[0, 0, 0], #undef, [0.0, 0.0, 0.0], [0.0, 0.0, 0.0], nothing)

```
