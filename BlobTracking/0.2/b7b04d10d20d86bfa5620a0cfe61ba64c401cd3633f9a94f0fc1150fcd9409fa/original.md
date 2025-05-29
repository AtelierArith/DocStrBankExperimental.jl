```
MCCorrespondence <: AbstractCorrespondence
```

Assigns blobs to measurement by approximately integrating over the posterior distribution over blobs and performing the assignment using the inner assignment

# Parameters

  * `inner`: inner assignment object
  * `num_samples::Int = 20` number of Monte Carlo samples to draw. The inner assignment routine will be called this many times so it can get expensive to set this too high.
