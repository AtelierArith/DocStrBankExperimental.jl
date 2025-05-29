A phase type to create the simulation state

# Fields

  * `name`: the name of the phase
  * `time_start`: the initial simulation time
  * `final_measures`: the measurements to make at the end of the phase see `measure` and `output`
  * `type`: the type of state to create `Pure()` or `Mixed()`
  * `system`: a System object to describe the system (see `System`) (unused if a State object is given)
  * `state`: a description of the state (or a State object)
  * `randomize`: the link dimension for the random state to create (default 0 for no randomizing)

# Examples

```
CreateState(type = Pure(), system = System(10, Qubit()), state = "Up")
CreateState(type = Mixed(), system = System(3, Qubit()), state = ["Up", "Dn", "Up])
CreateState(type = Pure(), system = System(10, Qubit()), randomize = 50)
CreateState(type = Pure(), system = System(10, Qubit()), state = "Up", randomize = 50)
CreateState(Pure(), 10, Qubit(), "Up")                                      # simple form
CreateState(Mixed(), [Qubit(), Boson(4), Fermion()], ["Up", "2", "Occ"])    # other simple form
```
