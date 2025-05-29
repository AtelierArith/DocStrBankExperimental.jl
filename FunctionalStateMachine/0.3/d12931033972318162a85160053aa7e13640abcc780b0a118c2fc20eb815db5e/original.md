```julia
mutable struct StateMachine{T}
```

Generic state machine functor type.

Example

```julia
bar!(usrdata) = IncrementalInference.exitStateMachine
foo!(usrdata) = bar!

sm = StateMachine(next=foo!)
usrdata = nothing
while st(usrdata); end
```

Notes

  * Also see IncrementalInference/test/testStateMachine.jl
