```
apply(m, i; kwargs...)::outputtype(m)
apply(m, d; kwargs...)::AbstractVector{<:outputtype(m)}
apply(m, d, i_instance; kwargs...)::outputtype(m)
```

Return the output prediction of a model `m` on a logical interpretation `i`, on the `i_instance` of a dataset `d`, or on all instances of a dataset `d`. Note that predictions can be `nothing` if the model is *open* (e.g., if the model is a `Rule`).

# Keyword Arguments

  * `check_args::Tuple = ()`;
  * `check_kwargs::NamedTuple = (;)`;
  * `functional_args::Tuple = ()`;
  * `functional_kwargs::NamedTuple = (;)`;
  * Any additional keyword argument is passed down to the model subtree's leaves

`check_args` and `check_kwargs` can influence check's behavior at the time of its computation (see [`SoleLogics.check](@ref))

`functional_args` and `functional_kwargs` can influence FunctionModel's behavior when the corresponding function is applied to AbstractInterpretation (see [`FunctionModel`](@ref), [`SoleLogics.AbstractInterpretation](@ref))

A model state-changing version of the function, [`apply!`], exist. While producing the output, this function affects the info keys `:supporting_labels` and `:supporting_predictions`, which are useful for inspecting the statistical performance of parts of the model.

See also [`isopen`](@ref), [`readmetrics`](@ref). [`AbstractModel`](@ref), [`SoleLogics.AbstractInterpretation`](@ref), [`SoleLogics.AbstractInterpretationSet`](@ref).
