```
transcription_constraint(model::JuMP.Model,
    cref::InfiniteOpt.InfOptConstraintRef;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Return the transcribed constraint reference(s) corresponding to `cref`. Errors if `cref` has not been transcribed. Also can query via the syntax:

```julia
transcription_constraint(cref::InfiniteOpt.InfOptConstraintRef;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

If the infinite model contains a built transcription model. By default, this method returns only transcribed constraints associated with public supports. All the  constraints can be returned by setting `label = All`.

If `cref` is infinite and `ndarray = true` then an n-dimensional array will be  returned in accordance with the infinite parameters that have unique object  numbers. In this case, `label` will be used to search the intersection of the supports that use the label. This is defers from the default behavior which  considers the union.

**Example**

```julia-repl
julia> transcription_constraint(trans_model, fin_con)
fin_con : x(support: 1) - y <= 3.0

julia> transcription_constraint(fin_con)
fin_con : x(support: 1) - y <= 3.0
```
