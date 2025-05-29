```julia
ScheduledMixing(VIn::N, VOut::N, F::T ; F_args::Tuple = (), F_kwargs::Dict = Dict() , alpha::Float64 = 0.5, iter::Int64 = 1, max_iter::Int64 = 1, Scheduler :: R = QuadraticScheduling, _extra...) --> Dict   where {T<:Function, N<:Union{Number, Vector{<:Number}}, R<:Function}
```

Returns a dictionary containing the following

  * "VInNext" : Simple mixing of VIn and VOut with weight (1-beta) and beta respectively, where beta = `Scheduler(alpha)`, which may change with iteration.
  * "VOutNext" : The function `F` evaluated at VInNExt, with fixed args `F_args` and kwargs `F_kwargs`.
  * "Delta" : The norm difference b/w the next input and output.
  * "kwargs" : the kwargs of this function itself, to be used by a subsequent function call in the next fixed point iteration. Here, the alpha value is updated every iteration using a Scheduler.
