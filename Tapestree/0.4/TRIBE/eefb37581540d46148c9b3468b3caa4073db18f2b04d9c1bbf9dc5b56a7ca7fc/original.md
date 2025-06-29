```
tribe(tree_file   ::String,
      data_file   ::String,
      out_file    ::String;
      min_dt      ::Float64           = 0.01,
      niter       ::Int64             = 50_000,
      nburn       ::Int64             = 50_000,
      nthin       ::Int64             = 500,
      saveXY      ::Tuple{Bool,Int64} = (false, 1_000),
      saveDM      ::Tuple{Bool,Int64} = (false, 1_000),
      ωxprior     ::NTuple{2,Float64} = (0.,10.),
      ω1prior     ::NTuple{2,Float64} = (0.,10.),
      ω0prior     ::NTuple{2,Float64} = (0.,10.),
      σ²prior     ::Float64           = 1e-1,
      λprior      ::Float64           = 1e-1,
      weight      ::NTuple{5,Float64} = (0.15,0.05,0.02,0.02,5e-3),
      λ1i         ::Float64           = 1.0,
      λ0i         ::Float64           = 0.5,
      ωxi         ::Float64           = 0.0,
      ω1i         ::Float64           = 0.0,
      ω0i         ::Float64           = 0.0,
      fix_ωx      ::Bool              = false,
      fix_ω1      ::Bool              = false,
      fix_ω0      ::Bool              = false,
      delim       ::Char              = '	',
      eol         ::Char              = '',
      screen_print::Int64             = 5)
```

Run **tribe** model. 

...

# Arguments

  * `tree_file::String`: full path to tree file.
  * `data_file::String`: full path to data file.
  * `out_file::String`: full path to write MCMC output.
  * `min_dt::Float64 = 0.01`: the percentage of tree height allowed for

discretization (lower values are more precise but take longer).

  * `niter::Int64 = 50_000`: the number of iterations.
  * `nburn::Int64 = 50_000`: the number of iterations in the adaptive burn-in phase.
  * `nthin::Int64 = 500`: the iteration sampling frequency.
  * `saveXY::Tuple{Bool,Int64} = (false, 1_000)`: first index to

save (or not) data augmented histories, second index for sampling frequency.

  * `saveDM::Tuple{Bool,Int64} = (false, 1_000)`: a tuple of length 2: first is a boolean to save (or not) data augmented deterministic effects, second an integer for sampling frequency.
  * `ωxprior::NTuple{2,Float64} = (0.,10.)`: a tuple of length 2 for the normal prior of ωx, first the mean, second the variance.
  * `ω1prior::NTuple{2,Float64} = (0.,10.)`: a tuple of length 2 for the normal prior of ω1, first the mean, second the variance.
  * `ω0prior::NTuple{2,Float64} = (0.,10.)`: a tuple of length 2 for the normal prior of ω0, first the mean, second the variance.
  * `σ²prior::Float64 = 1e-1`: a float for the mean of the exponential prior for σ².
  * `λprior::Float64 = 1e-1`: a float for the mean of the exponential prior for both λs.
  * `weight::NTuple{5,Float64} = (0.15,0.05,0.02,0.02,5e-3)`: a tuple of length 5 specifying the probabilities to update σ², ωx, ω1 & ω0, and λ1 & λ0 respectively.
  * `λ1i::Float64 = 1.0`: a float for the starting value for λ1.
  * `λ0i::Float64 = 0.5`: a float for the starting value for λ0.
  * `ωxi::Float64 = 0.0`: a float for the starting value for ωx.
  * `ω1i::Float64 = 0.0`: a float for the starting value for ω1.
  * `ω0i::Float64 = 0.0`: a float for the starting value for ω0.
  * `fix_ωx::Bool = false`: a boolean to make inference without ωx.
  * `fix_ω1::Bool = false`: a boolean to make inference without ω1.
  * `fix_ω0::Bool = false`: a boolean to make inference without ω0.
  * `delim::Char= '	'`: for ddlm.
  * `eol::Char= ' '`: for ddlm.
  * `screen_print::Int64 = 5`: seconds to wait to update screen log.

...

...

# Returned values

  * Array of the mcmc parameters.

...
