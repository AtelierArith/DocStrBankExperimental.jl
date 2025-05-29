```
struct State
State(Pure()|Mixed(), ::System, states)
State(Pure()|Mixed(), ::Int, ::AbstractSite, state)
State(Pure()|Mixed(), ::Vector{<:AbstractSite}, state)
State(::State, ::MPS)
```

represent the complete state of the simulated quantum system

# Fields

  * `type::Union{Pure, Mixed}`: pure or mixed representation
  * `system::System`: system description
  * `state::MPS`: system state
  * `preobs::PreObs`: preprocessing data for computing observables

# Examples

```
State(Pure(), system, "Up")
State(Mixed(), system, ["Up", "Dn", "Up"])
State(Mixed(), system, "FullyMixed")
State(Pure(), system, [1, 0])
State(Pure(), 10, Qubit(), "Up")
State(Mixed(), [Qubit(), Boson(4), Fermion()], ["Up", "2", "Occ"])
State(state, mps)        returns a new state with the same system but a new mps
```

# Operations

states can be added, substracted and multiplied by numbers
