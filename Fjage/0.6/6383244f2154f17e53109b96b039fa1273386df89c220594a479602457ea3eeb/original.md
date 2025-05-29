```
after(action, b::FSMBehavior, delay)
```

Schedule an action to be executed after a delay (in seconds). The scheduled action is automatically canceled when the FSM exits the current state.
