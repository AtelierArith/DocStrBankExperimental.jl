compressMPO!(W[,sweeps=,cutoff=,deltam=,minsweep=,nozeros=])

compresses an array of MPOs (`W`) in parallel with SVD compression for `sweeps` sweeps, `cutoff` applied to the SVD, `deltam` target for teh bond dimension compression, and `nozeros` defaulted to true to eliminate all zeros in the SVD
