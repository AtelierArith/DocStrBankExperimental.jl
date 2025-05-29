```
MCMCOptionsList(;
numiters = 5000,
burnin = floor(0.2 * numiters),
thin = 1,
numGibbs = 5,
numMH = 1)

List of options for running the MCMC.

# Constructor arguments
- `numiters::Integer`: number of iterations to run.
- `burnin::Integer`: number of iterations to discard as burn-in.
- `thin::Integer`: will keep every `thin` samples.
- `numGibbs:Integer`: number of intermediate Gibbs scans in the split-merge step.
- `numMH:Integer`: number of split-merge steps per MCMC iteration.
```
