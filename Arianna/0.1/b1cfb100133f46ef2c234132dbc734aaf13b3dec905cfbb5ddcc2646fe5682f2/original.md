```
Metropolis(chains; pool=missing, sweepstep=1, seed=1, R=Xoshiro, parallel=false, extras...)
```

Create a new Metropolis instance.

# Arguments

  * `chains`: Vector of systems to run the algorithm on
  * `pool`: Pool of moves to perform sweeps over
  * `sweepstep`: Number of Monte Carlo steps per sweep
  * `seed`: Random number seed
  * `R`: Type of the random number generator
  * `parallel`: Flag to parallelise over different threads
  * `extras`: Additional keyword arguments

# Returns

  * `algorithm`: Metropolis instance
