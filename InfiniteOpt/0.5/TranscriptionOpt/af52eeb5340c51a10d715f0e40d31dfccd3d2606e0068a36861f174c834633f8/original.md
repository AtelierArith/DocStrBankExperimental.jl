```
transcription_variable(model::JuMP.Model,
    vref::InfiniteOpt.GeneralVariableRef;
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
     ndarray::Bool = false])
```

Return the transcribed variable reference(s) corresponding to `vref`. Errors if no transcription variable is found. Also can query via the syntax:

```julia
transcription_variable(vref::InfiniteOpt.GeneralVariableRef; 
    [label::Type{<:InfiniteOpt.AbstractSupportLabel} = InfiniteOpt.PublicLabel,
     ndarray::Bool = false])
```

If the infinite model contains a built transcription model. By default, this method returns only transcribed variables associated with public supports. All the  variables can be returned by setting `label = All`. 

If `vref` is infinite and `ndarray = true` then an n-dimensional array will be  returned in accordance with the infinite parameters that have unique object  numbers. In this case, `label` will be used to search the intersection of variable  supports that use the label. This is defers from the default behavior which  considers the union.

**Example**

```julia-repl
julia> transcription_variable(trans_model, infvar)
2-element Array{VariableRef,1}:
 infvar(support: 1)
 infvar(support: 2)

julia> transcription_variable(trans_model, hdvar)
hdvar

julia> transcription_variable(infvar)
2-element Array{VariableRef,1}:
 infvar(support: 1)
 infvar(support: 2)

julia> transcription_variable(hdvar)
hdvar
```
