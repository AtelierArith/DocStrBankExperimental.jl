```
Recurrence(cell;
    ordering::AbstractTimeSeriesDataBatchOrdering=BatchLastIndex(),
    return_sequence::Bool=false)
```

Wraps a recurrent cell (like [`RNNCell`](@ref), [`LSTMCell`](@ref), [`GRUCell`](@ref)) to automatically operate over a sequence of inputs.

!!! warning "Relation to `Flux.Recur`"
    This is completely distinct from `Flux.Recur`. It doesn't make the `cell` stateful, rather allows operating on an entire sequence of inputs at once. See [`StatefulRecurrentCell`](@ref) for functionality similar to `Flux.Recur`.


## Arguments

  * `cell`: A recurrent cell. See [`RNNCell`](@ref), [`LSTMCell`](@ref), [`GRUCell`](@ref), for how the inputs/outputs of a recurrent cell must be structured.

## Keyword Arguments

  * `return_sequence`: If `true` returns the entire sequence of outputs, else returns only the last output. Defaults to `false`.
  * `ordering`: The ordering of the batch and time dimensions in the input. Defaults to `BatchLastIndex()`. Alternatively can be set to `TimeLastIndex()`.

# Extended Help

## Inputs

  * If `x` is a

      * Tuple or Vector: Each element is fed to the `cell` sequentially.
      * Array (except a Vector): It is spliced along the penultimate dimension and each slice is fed to the `cell` sequentially.

## Returns

  * Output of the `cell` for the entire sequence.
  * Update state of the `cell`.

!!! tip
    Frameworks like Tensorflow have special implementation of [`StackedRNNCells`](https://www.tensorflow.org/api_docs/python/tf/keras/layers/StackedRNNCells) to handle sequentially composed RNN Cells. In Lux, one can simple stack multiple `Recurrence` blocks in a `Chain` to achieve the same.

    ```
    Chain(
        Recurrence(RNNCell(inputsize => latentsize); return_sequence=true),
        Recurrence(RNNCell(latentsize => latentsize); return_sequence=true),
        :
        x -> stack(x; dims=2)
    )
    ```

    For some discussion on this topic, see https://github.com/LuxDL/Lux.jl/issues/472.

