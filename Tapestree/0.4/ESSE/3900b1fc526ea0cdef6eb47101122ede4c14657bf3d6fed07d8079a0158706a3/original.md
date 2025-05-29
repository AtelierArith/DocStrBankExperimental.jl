```
esse(tv          ::Dict{Int64,Array{Float64,1}},
     ed          ::Array{Int64,2}, 
     el          ::Array{Float64,1}, 
     x           ::Array{Float64,1},
     y           ::Array{Float64,L}, 
     cov_mod     ::NTuple{M,String},
     out_file    ::String,
     h           ::Int64;
     constraints ::NTuple{N,String}  = (" ",),
     mvpars      ::NTuple{O,String}  = ("lambda = beta",),
     niter       ::Int64             = 10_000,
     nthin       ::Int64             = 10,
     nburn       ::Int64             = 200,
     ncch        ::Int64             = 1,
     ntakew      ::Int64             = 100,
     winit       ::Float64             = 2.0,
     scale_y     ::NTuple{2,Bool}    = (true, false),
     algorithm   ::String            = "pruning",
     λpriors     ::Float64           = .1,
     μpriors     ::Float64           = .1,
     gpriors     ::Float64           = .1,
     lpriors     ::Float64           = .1,
     qpriors     ::Float64           = .1,
     βpriors     ::NTuple{2,Float64} = (0.0, 10.0),
     hpriors     ::Float64           = .1,
     optimal_w   ::Float64           = 0.8,
     screen_print::Int64             = 5,
     Eδt         ::Float64           = 1e-3,
     ti          ::Float64           = 0.0,
     ρ           ::Array{Float64,1}  = [1.0]) where {L,M,N,O}
```

Wrapper for running a **esse** model from simulations.
