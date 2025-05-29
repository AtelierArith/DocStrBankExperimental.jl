```
State(func)

State() do state
  ....
  return value, newstate
end
```

State monad, which capsulate a state within a monadic type for monadic encapsulation of the state-handling.

You can run a state by either calling it, or by using `Base.run`. If no initial state is given, `nothing` is used.
