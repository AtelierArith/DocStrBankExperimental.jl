```
BidirectionalRNN(cell::AbstractRecurrentCell,
    backward_cell::Union{AbstractRecurrentCell, Nothing}=nothing;
    merge_mode::Union{Function, Nothing}=vcat,
    ordering::AbstractTimeSeriesDataBatchOrdering=BatchLastIndex())
```

Bidirectional RNN wrapper.

## Arguments

  * `cell`: A recurrent cell. See [`RNNCell`](@ref), [`LSTMCell`](@ref), [`GRUCell`](@ref), for how the inputs/outputs of a recurrent cell must be structured.
  * `backward_cell`: A optional backward recurrent cell. If `backward_cell` is `nothing`, the rnn layer instance passed as the `cell` argument will be used to generate the backward layer automatically. `in_dims` of `backward_cell` should be consistent with `in_dims` of `cell`

## Keyword Arguments

  * `merge_mode`: Function by which outputs of the forward and backward RNNs will be combined. default value is `vcat`. If `nothing`, the outputs will not be combined.
  * `ordering`: The ordering of the batch and time dimensions in the input. Defaults to `BatchLastIndex()`. Alternatively can be set to `TimeLastIndex()`.

# Extended Help

## Inputs

  * If `x` is a

      * Tuple or Vector: Each element is fed to the `cell` sequentially.
      * Array (except a Vector): It is spliced along the penultimate dimension and each slice is fed to the `cell` sequentially.

## Returns

  * Merged output of the `cell` and `backward_cell` for the entire sequence.
  * Update state of the `cell` and `backward_cell`.

## Parameters

  * `NamedTuple` with `cell` and `backward_cell`.

## States

  * Same as `cell` and `backward_cell`.
