```
FilteringProblem(state_model, obs_model)
```

Specify a filtering problem for a hidden state model `state_model` and observation model `obs_model`.

Constraints: `state_model` and `obs_model` must be chosen such that

  * `state_model` is of type `HiddenStateModel{S1, T1}`,
  * `obs_model` is of type `ObservationModel{S1, S2, T2}`,

where `T1<:TimeType`, `T2 <:TimeType`, and `S1`, `S2` are arbitrary. This ensures that the filtering problem can be evaluated, i.e. the hidden states are of appropriate type to generate observations.
