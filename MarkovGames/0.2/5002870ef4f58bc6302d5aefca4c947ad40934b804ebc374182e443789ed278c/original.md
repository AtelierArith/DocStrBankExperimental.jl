```
isterminal(m::Game, s)
```

Check if state `s` is terminal. If a state is terminal, no actions will be taken in it and no additional rewards will be accumulated. Thus, the value function at such a state is, by definition, zero.
