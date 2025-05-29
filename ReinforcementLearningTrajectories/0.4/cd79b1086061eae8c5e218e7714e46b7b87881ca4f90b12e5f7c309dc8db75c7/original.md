```
MultiplexTraces{names}(trace)
```

A special [`AbstractTraces`](@ref) which has exactly two traces of the same length. And those two traces share the header and tail part.

For example, if a `trace` contains elements between 0 and 9, then the first `trace_A` is a view of elements from 0 to 8 and the second one is a view from 1 to 9.

```
      ┌─────trace_A───┐
trace 0 1 2 3 4 5 6 7 8 9
        └────trace_B────┘
```

This is quite common in RL to represent `states` and `next_states`.
