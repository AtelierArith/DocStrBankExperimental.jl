```
function predict(
    uf::UnfoldModel,
    f::Vector{<:FormulaTerm},
    evts::Vector{<:DataFrame};
    overlap::Bool = true,
    kwargs...
)
```

Returns a predicted ("y_hat = X*b") `Array`.

  * `uf` is an `<:UnfoldModel`
  * `f` is a (vector of) formulas, typically `Unfold.formulas(uf)`, but formulas can be modified e.g. by `effects`.
  * `evts` is a (vector of) events, can be `Unfold.events(uf)` to return the (possibly continuous-time) predictions of the model. Can be a custom even

## kwargs:

if `overlap = true` (default), overlap based on the `latency` column of `evts` will be simulated, or in the case of `!ContinuousTimeTrait` just X*coef is returned.

if `overlap = false`, returns predictions without overlap (models with `ContinuousTimeTrait` (=> with basisfunction / deconvolution) only), via `predict_no_overlap`

if `keep_basis` or `exclude_basis` is defined, then `predict_partial_overlap` is called, which allows to selective introduce overlap based on specified (or excluded respective) events/basisfunctions

`epoch_to` and  `epoch_timewindow`: calculate (partial) overlap controlled predictions, but returns them at the specified `epoch_at` event, with the times `epoch_timewindow` (default is taken from the basisfunction) in samples.

`eventcolumn` can be specified as well if different from the default `event`.

Hint: all `kwargs` can be `Vector`, or if e.g. `string` types are provided, will be put into a `length==1` vector.

## Output

  * If `overlap=false`, returns a 3D-Array
  * If `overlap=true` and `epoch_to = nothing` (default), returns a 2D-array
  * If `overlap=true` and `epoch_to != nothing`, returns a 3D array
