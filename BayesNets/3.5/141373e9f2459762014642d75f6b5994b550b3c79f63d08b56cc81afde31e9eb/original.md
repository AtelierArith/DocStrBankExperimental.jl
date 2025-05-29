Approximates p(query|evidence) with `nsamples` likelihood weighted samples.

Since this uses a Factor, it is only efficient if the number of samples is (signifcantly) greater than the number of possible instantiations for the query variables
