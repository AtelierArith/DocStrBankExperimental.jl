```
StatefulRecurrentCell(cell)
```

Wraps a recurrent cell (like [`RNNCell`](@ref), [`LSTMCell`](@ref), [`GRUCell`](@ref)) and makes it stateful.

To avoid undefined behavior, once the processing of a single sequence of data is complete, update the state with `Lux.update_state(st, :carry, nothing)`.

## Arguments

  * `cell`: A recurrent cell. See [`RNNCell`](@ref), [`LSTMCell`](@ref), [`GRUCell`](@ref), for how the inputs/outputs of a recurrent cell must be structured.

## Inputs

  * Input to the `cell`.

## Returns

  * Output of the `cell` for the entire sequence.
  * Update state of the `cell` and updated `carry`.

## States

  * NamedTuple containing:

      * `cell`: Same as `cell`.
      * `carry`: The carry state of the `cell`.
