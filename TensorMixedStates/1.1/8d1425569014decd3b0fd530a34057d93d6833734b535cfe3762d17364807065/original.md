```
type System
```

represent a quantum system

# Fields

  * `sites::Vector{<:AbstractSite}`: sites of the system
  * `pure_indices::Vector{Index}`: Indices for pure representations
  * `mixed_indices::Vector{Index}`: Indices for mixed representations

# Examples

```
System(10, Qubit())
System([Qubit(), SpinOne(), Qubit(), Boson(5)])
```

# Indexation

```
system[i]          gives site i
system[Pure(), i]  gives pure index i
system[Mixed(), i] gives mixed index i
```
