```
update!(fcm::FuzzyCognitiveMap)
```

Perform a single state update step on the `fcm`.

Updates the state of non-external concepts using the formula: `new_state = activation(state * weights)`

If track_history is enabled, the new state is added to the history.

# Arguments

  * `fcm::FuzzyCognitiveMap`: The FCM to update
