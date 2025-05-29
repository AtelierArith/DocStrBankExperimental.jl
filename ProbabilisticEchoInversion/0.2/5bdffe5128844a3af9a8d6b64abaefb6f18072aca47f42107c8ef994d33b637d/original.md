```
MAPMCMCSolver([;optimizer, options])
```

Construct an `MAPMCMCSolver`, specifying how to invert a probabilistic backscattering model using a combination of maximum a posteriori optimization and Markov-chain Monte  Carlo. This simply means that an optimization routine finds the MAP point estimate of the parameters, which is then used as the starting point for the MCMC run.

Arguments correspond exactly to the ones for `MAPSolver` and `MCMCSolver`; refer to  their documentation for details.
