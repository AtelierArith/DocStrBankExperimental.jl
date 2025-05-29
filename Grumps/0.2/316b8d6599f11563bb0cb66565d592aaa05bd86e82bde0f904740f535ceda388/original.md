```
OptimizationOptions(; 
θopt = OptimOptionsθ(), 
δopt = OptimOptionsδ(), 
threads = GrumpsThreads(), 
memsave = false, 
maxrepeats = 4, 
probtype = :fast,
id = :Grumps,
progressbar = false,
loopvectorization = true
)
```

Sets the options used for numerical optimization.  *θopt* is used for the external optimization routine, *δopt* for the internal one.  These are both of type *OptimOptions*; see the *OptimOptionsθ* and *OptimOptionsδ* methods for elaboration.  The *memsave* variable is set to false by default; turning it on will reduce memory consumption significantly, but will also slow down computation.  The variable *maxrepeats* may disappear in the  future.  

There are two ways of computing choice probabilities: robust and fast, specified by passing *:robust* or *:fast* in *probtype*. Fast choice probabilities are the default for good reason.

The progress bar shows progress within an iteration in the form of colored circles at the top right hand corner of the screen. The progress bar is turned off by default and should be off if Grumps is run without a terminal (e.g. in a batch script run on PBS or Slurm). Loop vectorization is a new addition to Grumps and speeds up computation in most cases.

Finally, specifying id allows one to add callbacks, e.g. user functions that are called on each inner and  outer iteration.  See the [Extending Grumps](@ref) portion of the documentation.
