```julia
BroydenMixing(VIn::N, VOut::N, F::T ; F_args::Tuple = (), F_kwargs::Dict = Dict() , alpha::Float64 = 0.5, B::Z = alpha*Matrix(1.0I, length(VIn), length(VIn)), _extra...) --> Dict where {T<:Function, N<:Union{Number, Vector{<:Number}}, Z<:Union{Number,Matrix{<:Number}}}
```

Returns a dictionary containing the following

  * "VInNext" : simple mixing of VIn and VOut with weight (1-beta) and beta respectively, where beta = `Scheduler(alpha)`, which may change with iteration.
  * "VOutNext" : The function `F` evaluated at VInNExt, with fixed args `F_args` and kwargs `F_kwargs`.
  * "Delta" : The norm difference b/w the next input and output.
  * "kwargs" : the kwargs of this function itself, to be used by a subsequent function call in the next fixed point iteration. Here, the B-matrix is updated every iteration according to Broyden mixing rules.
