```
transcription_expression(
    model::JuMP.Model,
    expr::JuMP.AbstractJuMPScalar;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
    ndarray::Bool = false])
```

Return the transcribed expression(s) corresponding to `expr`. Errors if `expr` cannot be transcribed. Also can query via the syntax:

```julia
transcription_expression(expr::JuMP.AbstractJuMPScalar;
                         [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
                         ndarray::Bool = false])
```

If the infinite model contains a built transcription model. By default, this method returns only transcribed expressions associated with public supports. All the  expressions can be returned by setting `label = All`.

If `expr` is infinite and `ndarray = true` then an n-dimensional array will be  returned in accordance with the infinite parameters that have unique object  numbers. In this case, `label` will be used to search the intersection of the supports that use the label. This is defers from the default behavior which  considers the union.

**Example**

```julia-repl
julia> transcription_expression(trans_model, my_expr)
x(support: 1) - y

julia> transcription_expression(my_expr)
x(support: 1) - y
```
