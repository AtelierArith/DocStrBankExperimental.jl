function dedup!(a,b)

Remove values of `a` that are duplicates. Remove values of `b` that have the same location as the duplicates in `a`. The length of `a` and `b` should be identical before and after invoking this function. 

# Arguments

  * `a::Vector{T}`: a density variable
  * `b::Vector{T}`: an accompanying tracer variable

Arguments are mutated by the function. 
