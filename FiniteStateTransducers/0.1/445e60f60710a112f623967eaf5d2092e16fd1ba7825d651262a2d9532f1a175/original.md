`Arc(ilab::Int,olab::Int,w::W,n::Int)`

Constructs an arc with input label `ilab`, output label `olab`, weight 'weight' and nextstate `n`. `ilab` and `olab` must be integers consistent with a input/output symbol table of the WFST at use.

Mainly used for internals see [`add_arc!`](@ref) for a simpler way of adding arcs to a WFST.   
