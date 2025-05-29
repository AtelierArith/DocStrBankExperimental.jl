function mixinversions!(a,b)

For values of `a` that are not increasing,  an inversion is defined. Average these values of a until values of `a` are sorted. Do the same averaging on the accompanying vector `b`.

# Arguments

  * `a::Vector{T}`: a density variable
  * `b::Vector{T}`: an accompanying tracer variable

Arguments are mutated by the function. 
