lsoda(f::Function, y0::Vector{Float64}, tspan::Vector{Float64}; userdata::Any=nothing, reltol::Union{Float64,Vector}=1e-4, abstol::Union{Float64,Vector}=1e-10)

Solves a set of ordinary differential equations using the LSODA algorithm. The vector field encoded in an inplace f::Function needs to have the self-explanatory arguments f(t, y, ydot, data)
