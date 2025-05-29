The Metropolis-Adjusted Langevin Algorithm (MALA). 

MALA is based on an approximation to overdamped Langevin dynamics followed by a  Metropolis-Hastings correction to ensure that we target the correct distribution.

This round-based version of MALA allows for the use of a preconditioner,  which is updated after every PT tuning round.  This setting can also be turned off by specifying the type of preconditioner to use.   However, MALA will not automatically adjust the step size.  For such functionality, use autoMALA.

As for autoMALA, the number of steps per exploration is `base_n_refresh * ceil(Int, dim^exponent_n_refresh)`. 
