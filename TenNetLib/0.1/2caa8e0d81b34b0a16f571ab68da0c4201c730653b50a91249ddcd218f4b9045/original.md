```
struct CouplingModel{T}
    sites::Vector{Index{T}}
    terms::Vector{IDTensors}
end
```

`CouplingModel` for a given `OpStrings` Hamiltonian terms and `sites::Vector{Index}`.

  * `sites::Vector{Index{T}}`: Site `Index`s.
  * `terms::Vector{IDTensors}`: Collection of Hamiltonian terms.
