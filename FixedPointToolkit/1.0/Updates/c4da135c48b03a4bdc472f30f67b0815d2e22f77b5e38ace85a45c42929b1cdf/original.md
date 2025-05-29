```julia
SimpleMixing(VIn::N, VOut::N, F::T ; F_args::Tuple = (), F_kwargs::Dict = Dict() , alpha::Float64 = 0.5, _extra...) --> Dict   where {T<:Function, N<:Union{Number, Vector{<:Number}}}
```

Returns a dictionary containing the following

  * "VInNext" : Simple mixing of VIn and VOut with weight (1-`alpha`) and `alpha` respectively.
  * "VOutNext" : The function `F` evaluated at VInNExt, with fixed args `F_args` and kwargs `F_kwargs`.
  * "Delta" : The norm difference b/w the next input and output.
  * "kwargs" : the kwargs of this function itself, to be used by a subsequent function call in the next fixed point iteration. Since this is simple mixing, `alpha` is held constant.
