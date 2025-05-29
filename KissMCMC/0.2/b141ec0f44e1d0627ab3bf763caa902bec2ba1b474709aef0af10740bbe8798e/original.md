```
squash_walkers(thetas, accept_ratio, blobs, logdensities;
                                                     drop_low_accept_ratio=false,
                                                     drop_fact=2,
                                                     verbose=true,
                                                     order=false, # if true the samples are ordered, this may not work with blobs not stored in vectors
                                                     merge_blobs!=append!) # function to merge one blobs into another blobs (blobs1, blobs1) -> merge blobs2 into blobs1
```

Puts the samples of all emcee walkers into one vector.

This can also drop walkers which have a low accept ratio (this can happen with emcee, but I am anything but sure whether this is ok), by setting drop*low*accept*ratio=true.  drop*fact -> increase to drop more walkers.

Returns:

  * thetas
  * mean(accept_ratio[walkers2keep])
  * log-densities
  * blobs
