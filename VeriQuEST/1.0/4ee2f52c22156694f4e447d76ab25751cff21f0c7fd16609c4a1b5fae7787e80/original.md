```
init_qubit(::DummyQubit)::Int64
```

This function is used to initialize the qubit in the meta graph.  The state is not given, but the bit for the initial state of the dummy qubit is returned.

# Arguments

  * `dummy::DummyQubit`: The DummyQubit object.

# Returns

  * An Int64 representing the bit for the initial state of the dummy qubit.

# Examples

`julia dummy = DummyQubit() bit = init_qubit(dummy)``
