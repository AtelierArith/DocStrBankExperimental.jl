```
get_rotation(site_index, ensemble="Haar")
```

Generate a single-qubit unitary sampled from a specified ensemble.

# Arguments:

  * `site_index::Index{Int64}`: Site index.
  * `ensemble::String`: Type of unitary ensemble (`"Haar"`, `"Pauli"`, `"Identity"`).

# Returns:

  * An `ITensor` representing the unitary transformation.

# Example:

```julia
U = get_rotation(site_index, "Pauli")
```
