```
esse(tree_file   ::String,
     out_file    ::String,
     h           ::Int64;
     states_file ::String            = "NaN",
     envdata_file::String            = "NaN",
     cov_mod     ::NTuple{M,String}  = ("",),
     node_ps     ::Tuple{Bool,Int64} = (true, 10),
     out_states  ::String            = "",
     constraints ::NTuple{N,String}  = (" ",),
     mvpars      ::NTuple{O,String}  = (" ",),
     niter       ::Int64             = 10_000,
     nthin       ::Int64             = 10,
     nburn       ::Int64             = 200,
     tune_int    ::Int64             = 100,
     nswap       ::Int64             = 10,
     ncch        ::Int64             = 1,
     parallel    ::Bool              = ncch > 1,
     dt           ::Float64          = 0.2,
     ntakew      ::Int64             = 100,
     winit       ::Float64           = 2.0,
     scale_y     ::NTuple{2,Bool}    = (true, false),
     algorithm   ::String            = "pruning",
     mc          ::String            = "slice",
     λpriors     ::Float64           = .1,
     μpriors     ::Float64           = .1,
     gpriors     ::Float64           = .1,
     lpriors     ::Float64           = .1,
     qpriors     ::Float64           = .1,
     βpriors     ::NTuple{2,Float64} = (0.0, 10.0),
     hpriors     ::Float64           = .1,
     optimal_w   ::Float64           = 0.8,
     tni         ::Float64           = 1.0,
     obj_ar      ::Float64           = 0.6,
     screen_print::Int64             = 5,
     Eδt         ::Float64           = 1e-3,
     ti          ::Float64           = 0.0,
     ρ           ::Array{Float64,1}  = [1.0]) where {M,N,O}
```

Run geographic **esse**. See tutorial for how these files should be specified.

# Arguments

  * `tree_file::String`: full path to tree file.
  * `out_file::String`: full path to write MCMC output.
  * `h::Int64`: number of hidden states.
  * `states_file ::String = "NaN"`: full path to states file. If `"NaN"`, no

observed states are used (only hidden states).

  * `envdata_file::String = "NaN"`: full path to covariates file. If `"NaN"`, no

covariates are used (i.e., constant rates).

  * `cov_mod::NTuple{M,String} = ("",)`: specifies which rates are affected by

covariates: `s` for speciation, `e` for extinction, and `g` for colonization. More than 1 is possible.

  * `node_ps::Tuple{Bool,Int64} = (true, 10)`: first index specifies if posterior

marginal probabilities for nodes should be computed, second index the number of iterations to be computed. 

  * `out_states::String = ""`: full path to write node probabilities output.
  * `constraints::NTuple{N,String} = (" ",)`: constraints for the model

parameters.

  * `mvpars::NTuple{O,String} = (" ",)`: which parameters should be multivariate

when using slice sampling for better convergence.

  * `niter::Int64 = 10_000`: number of iterations.
  * `nthin::Int64 = 10`: frequency at which to record MCMC state.
  * `nburn::Int64 = 200`: number of iterations to discard as burn-in.
  * `tune_int::Int64 = 100`: number of iterations during `nburn` to tune proposal

window for MH.

  * `nswap::Int64 = 10`: every iteration to try to swap chain likelihoods in MC3.
  * `ncch::Int64 = 1`: number of chains.
  * `parallel::Bool = false`: if parallel run.
  * `dt::Float64 = 0.2`: temperature for MC3.
  * `ntakew::Int64 = 100`: number of iterations from `nburn` to tune the window

for slice sampling.

  * `winit::Float64 = 2.0`: initial window for slice sampling.
  * `scale_y::NTuple{2,Bool} = (true, false)`: first index if scale covariates `y`

to [0,1], second, if scale covariates `y` all together between [0,1].

  * `algorithm::String = "pruning"`: likelihood algorithm between `pruning`

(recommended) or `flow`.

  * `mc::String = "slice"`: which sampling `slice` (slice-sampling) or

`mh` (metropolis-hasting).

  * `λpriors::Float64 = 0.1`: rate of Exponential prior for speciation.
  * `μpriors::Float64 = 0.1`: rate of Exponential prior for global extinction.
  * `gpriors::Float64 = 0.1`: rate of Exponential prior for colonization.
  * `lpriors::Float64 = 0.1`: rate of Exponential prior for local extinction.
  * `qpriors::Float64 = 0.1`: rate of Exponential prior for hidden state

transitions.

  * `βpriors::NTuple{2,Float64} = (0.0, 10.0)`: mean and variance of Normal

prior for effect of covariates.

  * `hpriors::Float64 = 0.1`: rate of Exponential prior for differences between

hidden states.

  * `optimal_w::Float64 = 0.8`: optimal window.
  * `tni::Float64 = 1.0`: initial tuning for rates.
  * `obj_ar::Float64 = 0.23`: objective acceptance rate.
  * `screen_print::Int64 = 5`: seconds to wait to update screen log.
  * `Eδt::Float64 = 1e-3`: for flow algorithm.
  * `ti::Float64 = 0.0`: for flow algorithm.
  * `ρ::Array{Float64,1} = [1.0]`: sampling fraction for each state (each area and

widespread).

# Returned values

  * Array of the mcmc parameters.
