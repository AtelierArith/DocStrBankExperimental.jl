```
has_transition(A::AbstractAutomaton, t::AbstractTransition)::Bool
```

Returns a `Bool` indicating whether the automaton `A` has the transition `t`.

```
has_transition(A::AbstractAutomaton, q, r)::Bool
```

Returns a `Bool` indicating whether the automaton `A` has a transition from state `q` to state `r`.
