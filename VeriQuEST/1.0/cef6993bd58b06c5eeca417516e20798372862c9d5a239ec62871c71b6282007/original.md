```
compute_angle_δᵥ(mbqc, qubits, ϕ, Sx, Sz)
```

Compute the angle δᵥ for the given MBQC, qubits, ϕ, Sx, and Sz.

# Arguments

  * `mbqc`: The MBQC object.
  * `qubits`: The qubits object, either `NoInputQubits` or `InputQubits`.
  * `ϕ`: The angle ϕ.
  * `Sx`: The Sx value.
  * `Sz`: The Sz value.

# Returns

  * The updated angle δᵥ.

# Example

```julia
julia> compute_angle_δᵥ(MBQC(), NoInputQubits(), 0, 0, [0, 0, 0])
0
```
