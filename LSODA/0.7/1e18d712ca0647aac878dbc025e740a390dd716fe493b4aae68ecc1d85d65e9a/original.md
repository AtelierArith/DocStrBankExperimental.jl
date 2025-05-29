lsoda*evolve!(ctx::lsoda*context_t,y::Vector{Float64},tspan::Vector{Float64})

Solves a set of ordinary differential equations using the LSODA algorithm and the context variable ctx. This avoid re-allocating ctx. You have to be carefull to remember the current time or this function will return an error.
