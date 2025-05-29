```
makeswarm(;<keyword arguments>)
```

write swarm and fit files used on biowulf

#Arguments

  * 'nthreads=1`: number of Julia threads per processesor, default = 1
  * `swarmfile::String="fit"`: name of swarmfile to be executed by swarm
  * `juliafile::String="fitscript`: name of file to be called by julia in swarmfile
  * `src=""`: path to folder containing StochasticGene.jl/src (only necessary if StochasticGene not installed)

and all keyword arguments of function fit(; <keyword arguments> )

see fit

Note:: the keyword 'method' is handled slightly differently here than in the function fit.  In fit it is a function (i.e. numerical method function used in DifferentialEquations.jl) or a tuple of the numerical method and a Bool for hierarchical models.  However, in biowulf.jl, the numerical method must be a String, i.e. use "Tsit5()" for Tsit5().  This is because when Julia writes the function, it will parse the numerical method rather than just writing it.
