```
nextstate!(b::FSMBehavior, state::FSMState)
```

Set the next state of the FSM. Transition occurs after the current action is completed, if called from the action method for a state.
