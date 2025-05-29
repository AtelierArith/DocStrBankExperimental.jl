```
Node(position::Vector{Float64}, dofs::Vector{Bool}, id::Symbol = nothing)
```

Instantiate a 6 DOF node with given position and fixities. Optional symbol identifier, `id`.

# Example

```julia-repl
julia> Node([4.3, 2.2, 10.4], [true, true, false, true, false, false])
Node([4.3, 2.2, 10.4], Bool[1, 1, 0, 1, 0, 0], #undef, #undef, #undef, nothing)
```

---

```
Node(position::Vector{Float64}, fixity::Symbol, id::Symbol = nothing)
```

Instantiate a 6 DOF node with given position and common boundary type. Optional symbol identifier, `id`.

Available boundary conditions:

  * :free
  * :fixed
  * :pinned
  * :(x/y/z)free
  * :(x/y/z)fixed

# Example

```julia-repl
julia> Node([4.3, 2.2, 10.4], :zfixed)
Node([4.3, 2.2, 10.4], Bool[1, 1, 0, 1, 1, 1], #undef, #undef, #undef, nothing)

```
