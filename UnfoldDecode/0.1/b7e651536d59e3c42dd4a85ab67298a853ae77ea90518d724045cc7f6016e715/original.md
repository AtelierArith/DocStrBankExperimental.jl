```
Unfold.fit(
    UnfoldDecodingModel,
    design,
    tbl::DataFrame,
    dat::AbstractMatrix,
    model::MLJ.Model,
    target::Pair;
    nfolds = 6,
    eventcolumn = :event,
    unfold_fit_options = (;),
    multithreading = true,
)
```

Use `UnfoldDecodingModel` to apply overlap correction in a cross-validated way, and perform decoding on the resulting data

# Arguments

  * `design::`: An Unfold-design vector, e.g. `["eventA"=>(@formula(y~1+condition),firbasis((-0.1,1),100)]`
  * `tbl::DataFrame`: the events, as in a normal Unfold Model
  * `data::AbstractMatrix`:  the continuous EEG data, ch x time
  * `model::MLJModelInterface.Probabilistic`: By default LDA() is used, but could be other MLJ machines
  * `target::Pair`: A eventtype->column, String or Symbol pair, indicating which event and `tbl[:,column]` is the target to be decoded. E.g. `"eventA" => :condition`

# Keyword arguments

  * `nfolds::Int = 6`: number of cross-validation folds
  * `eventcolumn::Union{Symbol,String} = :event` - the column in `tbl` to differentiate the basisfunctions as defined in `design`
  * `unfold_fit_options`: optional `NamedTuple` of arguments, provided to the initial "overlap-cleaning" `Unfold.fit` function, e.g. `unfold_fit_options = (;solver=(x,y)->solver_krylov(x,y,GPU=true))` for GPU fit (need to load `Krylov` and `CUDA` before)
  * `multithreading::Bool = true`: Activate/deactivate multi-threading over time-points

# Returns

  * `result::UnfoldDecodingModel` : An Unfold-type model that you could inspect e.g. via `coef(result)`
