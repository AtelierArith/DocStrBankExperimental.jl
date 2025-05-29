```
`reinit!(:: AbstractState, :: T; kwargs...)`
```

Function that set all the entries at `_init_field` except the mandatory `x`.

Note: If `x` is given as a kargs it will be prioritized over the second argument.

Examples: `reinit!(state2, zeros(2))` `reinit!(state2, zeros(2), current_time = 1.0)`

There is a shorter version of reinit! reusing the `x` in the state

```
`reinit!(:: AbstractState; kwargs...)`
```

Examples: `reinit!(state2)` `reinit!(state2, current_time = 1.0)`
