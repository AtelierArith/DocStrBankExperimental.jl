```
TerminalState
```

A type with no fields whose singleton instance `terminalstate` is used to represent a terminal state with no additional information.

This type has the appropriate promotion logic implemented to function like `Missing` when added to arrays, etc.

Note that terminal states NEED NOT be of type `TerminalState`. You can define any state to be terminal by implementing the appropriate `isterminal` method. Solvers and simulators SHOULD NOT check for this type, but should instead check using `isterminal`. 
