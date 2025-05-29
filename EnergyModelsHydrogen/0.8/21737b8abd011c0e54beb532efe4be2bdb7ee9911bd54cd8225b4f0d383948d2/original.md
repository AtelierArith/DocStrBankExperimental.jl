```
struct CommitParameters
```

Type for providing parameters required in unit commitment constraints.

# Fields

  * **`opex::TimeProfile`** is the cost profile per installed capacity and operational duration if the node is within the state.
  * **`time::TimeProfile`** is the minimum time the node has to remain in the state before it can transition to the next state.
