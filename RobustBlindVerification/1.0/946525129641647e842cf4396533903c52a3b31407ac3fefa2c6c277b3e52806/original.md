````
MBQCFlow(forward_flow, backward_flow)

Struct representing flow in MBQC.

# Definition of Flow
- `forward_flow`, `f`: Oᶜ → Iᶜ is a mapping `v ↦ f(v)` with an inverse `f⁻¹(v) ↦ v`, with partial order "≤". The partial order is said to map the present to the future or the present to the past.
- (a) `v ∼ f(v)`, where "∼" defines the neighbourhood `N(f(v))` and `v` has set membership.
- (b) `v ≤ f(v)`
- (c) `w ∼ f(v)`, then ∀ `v`, `v ≤ w`

## Example
- One dimensional lattice, the "path graph", where a vertex is represented as "()" and an edge is represented as "---".
- Let `i` be the index of each vertex so that `i = {1, 2, 3, 4}` and
- `p := (1)---(2)---(3)---(4)`
- `f(i) := i + 1`
- `f⁻¹(i) := i - 1`
- `f([1, 2, 3]) = [2, 3, 4]`, since 4 has no future, there is no 4 + 1 answer.
- `f⁻¹([2, 3, 4]) = [1, 2, 3]`, since 1 has no past, there is no 1 - 1 answer.

# Parameters
- `forward_flow`: A mapping to take an input vertex and return the output vertex such that the definitions of flow hold. The forward flow function can be any container that takes a vertex index as input and outputs a new vertex index.
- `backward_flow`: A mapping to take an output vertex and return the input vertex. The backward flow function maps the inverse of the forward flow.

# Example
```julia
# Define forward and backward flow functions
forward_flow(io) = io[2]
backward_flow(io) = io[1]

# Create an MBQCFlow
mbqc_flow = MBQCFlow(forward_flow, backward_flow)
```
````
