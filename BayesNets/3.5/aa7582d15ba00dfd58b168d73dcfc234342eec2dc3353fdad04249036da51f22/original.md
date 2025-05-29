The GibbsSampler type houses the parameters of the Gibbs sampling algorithm.  The parameters are defined below:

burn*in:  The first burn*in samples will be discarded.  They will not be returned. The thinning parameter does not affect the burn in period. This is used to ensure that the Gibbs sampler converges to the target stationary distribution before actual samples are drawn.

thinning: For every thinning + 1 number of samples drawn, only the last is kept. Thinning is used to reduce autocorrelation between samples. Thinning is not used during the burn in period. e.g. If thinning is 1, samples will be drawn in groups of two and only the second sample will be in the output.

time*limit: The number of milliseconds to run the algorithm. The algorithm will return the samples it has collected when either nsamples samples have been collected or time*limit milliseconds have passed.  If time_limit is null then the algorithm will run until nsamples have been collected. This means it is possible that zero samples are returned.

error*if*time*out: If error*if*time*out is true and the time*limit expires, an error will be raised. If error*if*time*out is false and the time limit expires, the samples that have been collected so far will be returned.         This means it is possible that zero samples are returned.  Burn in samples will not be returned. If time_limit is null, this parameter does nothing.

consistent_with: the assignment that all samples must be consistent with (ie, Assignment(:A=>1) means all samples must have :A=1). Use to sample conditional distributions.

max*cache*size:  If null, cache as much as possible, otherwise cache at most "max*cache*size"  distributions

variable*order: variable*order determines the order of variables changed when generating a new sample. If null use a random order for every sample (this is different from updating the variables at random). Otherwise should be a list containing all the variables in the order they should be updated.

initial_sample:  The inital assignment to variables to use.  If null, the initial sample is chosen by briefly using a LikelihoodWeightedSampler.
